@expose("/<id_or_slug>/download_data", methods=("POST",))
def download_data(self, id_or_slug: str) -> Response:

    print("===== DOWNLOAD API HIT =====")
    print("Dashboard:", id_or_slug)

    dashboard = DashboardDAO.get_by_id_or_slug(id_or_slug)

    print("Dashboard Found:", dashboard.id)

    body = request.json or {}

    print("Request Body:", body)

    export_type = body.get("export_type", "csv")

    metadata = json.loads(dashboard.json_metadata or "{}")

    print("Metadata:", metadata)

    download_query = metadata.get("download_query")

    print("Download Query:", download_query)










    try:
    print("Executing Query:", download_query)

    result = db.session.execute(
        text(download_query)
    )

    print("Query Executed Successfully")

except Exception as ex:
    print("QUERY ERROR:", str(ex))

    return self.response(
        400,
        message=str(ex),
    )


















    rows = result.fetchall()

print("Rows Count:", len(rows))

columns = result.keys()

print("Columns:", list(columns))
