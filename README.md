         responses:
            200:
              description: Result contains the embedded dashboard config
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      result:
                        $ref: '#/components/schemas/EmbeddedDashboardResponseSchema'
            401:
              $ref: '#/components/responses/401'
            500:
              $ref: '#/components/responses/500'
        """
        if not dashboard.embedded:
            return self.response(404)
        embedded: EmbeddedDashboard = dashboard.embedded[0]
        result = self.embedded_response_schema.dump(embedded)
        return self.response(200, result=result)

    @expose("/<id_or_slug>/embedded", methods=["POST", "PUT"])
    @protect()
    @safe
    @statsd_metrics
    @event_logger.log_this_with_context(
        action=lambda self, *args, **kwargs: f"{self.__class__.__name__}.set_embedded",
        log_to_statsd=False,
    )
    @with_dashboard
    def set_embedded(self, dashboard: Dashboard) -> Response:
        """Set a dashboard's embedded configuration.
        ---
        post:
          summary: Set a dashboard's embedded configuration
          parameters:
          - in: path
            schema:
              type: string
            name: id_or_slug
            description: The dashboard id or slug
          requestBody:
            description: The embedded configuration to set
            required: true
            content:
              application/json:
                schema: EmbeddedDashboardConfigSchema
          responses:
            200:
              description: Successfully set the configuration
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      result:
                        $ref: '#/components/schemas/EmbeddedDashboardResponseSchema'
            401:
              $ref: '#/components/responses/401'
            500:
              $ref: '#/components/responses/500'
        put:
          description: >-
            Sets a dashboard's embedded configuration.
          parameters:
          - in: path
            schema:
              type: string
            name: id_or_slug
            description: The dashboard id or slug
          requestBody:
            description: The embedded configuration to set
            required: true
            content:
              application/json:
                schema: EmbeddedDashboardConfigSchema
          responses:
            200:
              description: Successfully set the configuration
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      result:
                        $ref: '#/components/schemas/EmbeddedDashboardResponseSchema'
            401:
              $ref: '#/components/responses/401'
            500:
              $ref: '#/components/responses/500'
        """
        try:
            body = self.embedded_config_schema.load(request.json)

            embedded = EmbeddedDashboardDAO.upsert(
                dashboard,
                body["allowed_domains"],
            )
            db.session.commit()  # pylint: disable=consider-using-transaction

            result = self.embedded_response_schema.dump(embedded)
            return self.response(200, result=result)
        except ValidationError as error:
            db.session.rollback()  # pylint: disable=consider-using-transaction
            return self.response_400(message=error.messages)

    @expose("/<id_or_slug>/embedded", methods=("DELETE",))
    @protect()
    @safe
    @permission_name("set_embedded")
    @statsd_metrics
    @event_logger.log_this_with_context(
        action=lambda self,
        *args,
        **kwargs: f"{self.__class__.__name__}.delete_embedded",
        log_to_statsd=False,
    )
    @with_dashboard
    def delete_embedded(self, dashboard: Dashboard) -> Response:
        """Delete a dashboard's embedded configuration.
        ---
        delete:
          summary: Delete a dashboard's embedded configuration
          parameters:
          - in: path
            schema:
              type: string
            name: id_or_slug
            description: The dashboard id or slug
          responses:
            200:
              description: Successfully removed the configuration
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      message:
                        type: string
            401:
              $ref: '#/components/responses/401'
            500:
              $ref: '#/components/responses/500'
        """
        DeleteEmbeddedDashboardCommand(dashboard).run()
        return self.response(200, message="OK")
    
    @expose("/<id_or_slug>/download_data", methods=("POST",))
    @protect()
    @safe
    @statsd_metrics
    def download_data(self, id_or_slug: str) -> Response:
        """
        Download dashboard data using configured SQL query.
        """

        from superset.daos.dashboard import DashboardDAO
        from superset.models.dashboard import Dashboard
        from superset import db

        dashboard = DashboardDAO.get_by_id_or_slug(id_or_slug)

        body = request.json or {}

        export_type = body.get("export_type", "csv")

        metadata = json.loads(dashboard.json_metadata or "{}")

        download_query = metadata.get("download_query")

        if not download_query:
            return self.response(
                400,
                message="No download query configured for this dashboard",
            )

        result = db.session.execute(download_query)

        rows = result.fetchall()

        columns = result.keys()

        df = pd.DataFrame(rows, columns=columns)

        output = BytesIO()

        if export_type == "excel":
            with pd.ExcelWriter(output, engine="openpyxl") as writer:
                df.to_excel(writer, index=False)

            output.seek(0)

            return send_file(
                output,
                mimetype="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
                as_attachment=True,
                download_name=f"{dashboard.dashboard_title}.xlsx",
            )

        df.to_csv(output, index=False)

        output.seek(0)

        return send_file(
            output,
            mimetype="text/csv",
            as_attachment=True,
            download_name=f"{dashboard.dashboard_title}.csv",
        )

    @expose("/<id_or_slug>/copy/", methods=("POST",))
    @protect()
    @safe
    @permission_name("write")
    @statsd_metrics
    @event_logger.log_this_with_context(
        action=lambda self, *args, **kwargs: f"{self.__class__.__name__}.copy_dash",
        log_to_statsd=False,
    )
    @with_dashboard
    def copy_dash(self, original_dash: Dashboard) -> Response:
        """Create a copy of an existing dashboard.
        ---
        post:
          summary: Create a copy of an existing dashboard
          parameters:
          - in: path
            schema:
              type: string
            name: id_or_slug
            description: The dashboard id or slug
          requestBody:
            required: true
            content:
              application/json:
                schema:
                  $ref: '#/components/schemas/DashboardCopySchema'
          responses:
            200:
              description: Id of new dashboard and last modified time
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      id:
                        type: number
                      last_modified_time:
                        type: number
            400:
              $ref: '#/components/responses/400'
            401:
              $ref: '#/components/responses/401'
            403:
              $ref: '#/components/responses/403'
            404:
              $ref: '#/components/responses/404'
            500:
              $ref: '#/components/responses/500'
        """
        try:
            data = DashboardCopySchema().load(request.json)
        except ValidationError as error:
            return self.response_400(message=error.messages)

        try:
            dash = CopyDashboardCommand(original_dash, data).run()
        except DashboardForbiddenError:
            return self.response_403()
        except DashboardCopyError:
            return self.response_400()

        return self.response(
            200,
            result={
                "id": dash.id,
                "last_modified_time": dash.changed_on.replace(
                    microsecond=0
                ).timestamp(),
            },
        )
