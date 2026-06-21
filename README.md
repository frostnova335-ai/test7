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
