import functools
import logging
from datetime import datetime
from io import BytesIO
import pandas as pd
from typing import Any, Callable, cast
from zipfile import is_zipfile, ZipFile

from flask import (current_app, g, redirect, request, Response, send_file, url_for, jsonify)

from flask_appbuilder import permission_name
from flask_appbuilder.api import expose, protect, rison, safe
from flask_appbuilder.models.sqla.interface import SQLAInterface
from flask_babel import gettext, ngettext
from sqlalchemy import text
from marshmallow import ValidationError
from werkzeug.wrappers import Response as WerkzeugResponse
from werkzeug.wsgi import FileWrapper

       "put_filters",
        "download_data",
        "put_colors",
    }


       result = self.dashboard_get_response_schema.dump(dash)

        metadata = json.loads(dash.json_metadata or "{}")

        result["download_query"] = metadata.get("download_query")

        add_extra_log_payload(
            dashboard_id=dash.id, action=f"{self.__class__.__name__}.get"
        )


        try:
            item = self.edit_model_schema.load(request.json)
            download_query = request.json.get("download_query")
        # This validates custom Schema with custom validations
        except ValidationError as error:
            return self.response_400(message=error.messages)
        try:
            changed_model = UpdateDashboardCommand(pk, item).run()



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

        result = db.session.execute(text(download_query))

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




