import pandas as pd

from io import BytesIO

from flask import send_file

from sqlalchemy import text



@expose("/<int:dashboard_id>/download-config", methods=("GET",))
@protect()
def get_download_config(self, dashboard_id):
    dashboard = db.session.query(Dashboard).get(dashboard_id)

    metadata = json.loads(dashboard.json_metadata or "{}")

    return self.response(
        200,
        result=metadata.get("download_config", {}),
    )
