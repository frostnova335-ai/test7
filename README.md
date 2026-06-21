from superset.models.dashboard import Dashboard


from superset.models.core import Database
import pandas as pd
from sqlalchemy import text



from flask import current_app, g, redirect, request, Response, send_file, url_forZ


from io import BytesIO



include_route_methods = RouteMethod.REST_MODEL_VIEW_CRUD_SET | {
    RouteMethod.EXPORT,
    RouteMethod.IMPORT,
    RouteMethod.RELATED,
    "bulk_delete",
    "favorite_status",
    "add_favorite",
    "remove_favorite",
    "get_charts",
    "get_datasets",
    "get_tabs",




        "get_download_config",
    "save_download_config",
    "download_dashboard_data",




    def get_charts(self, id_or_slug: str) -> Response:




    @expose("/<int:dashboard_id>/download-config", methods=("GET",))
@protect()
def get_download_config(self, dashboard_id: int) -> Response:
    dashboard = db.session.query(Dashboard).get(dashboard_id)

    if not dashboard:
        return self.response_404()

    metadata = json.loads(dashboard.json_metadata or "{}")

    return self.response(
        200,
        result=metadata.get("download_config", {}),
    )


@expose("/<int:dashboard_id>/download-config", methods=("POST",))
@protect()
@requires_json
def save_download_config(self, dashboard_id: int) -> Response:

    dashboard = db.session.query(Dashboard).get(dashboard_id)

    if not dashboard:
        return self.response_404()

    metadata = json.loads(dashboard.json_metadata or "{}")

    metadata["download_config"] = request.json

    dashboard.json_metadata = json.dumps(metadata)

    db.session.commit()

    return self.response(
        200,
        result="saved",
    )


@expose("/<int:dashboard_id>/download", methods=("POST",))
@protect()
@requires_json
def download_dashboard_data(self, dashboard_id: int):

    dashboard = db.session.query(Dashboard).get(
        dashboard_id
    )

    if not dashboard:
        return self.response_404()

    metadata = json.loads(
        dashboard.json_metadata or "{}"
    )

    config = metadata.get(
        "download_config"
    )

    if not config:
        return self.response_400(
            message="No download config found"
        )

    start_date = request.json.get(
        "start_date"
    )

    end_date = request.json.get(
        "end_date"
    )

    export_format = request.json.get(
        "format",
        "csv",
    )

    query = config["query"]

    query = query.replace(
        ":start_date",
        f"'{start_date}'",
    )

    query = query.replace(
        ":end_date",
        f"'{end_date}'",
    )

    database = db.session.query(
        Database
    ).get(
        config["database_id"]
    )

    engine = database.get_sqla_engine()

    df = pd.read_sql(
        text(query),
        engine,
    )

    output = BytesIO()

    if export_format == "csv":

        df.to_csv(
            output,
            index=False,
        )

        output.seek(0)

        return send_file(
            output,
            mimetype="text/csv",
            as_attachment=True,
            download_name="dashboard_export.csv",
        )

    df.to_excel(
        output,
        index=False,
    )

    output.seek(0)

    return send_file(
        output,
        mimetype="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
        as_attachment=True,
        download_name="dashboard_export.xlsx",
    )
