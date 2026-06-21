query_check = download_query.strip().lower()

if not query_check.startswith("select"):
    return self.response(
        400,
        message="Only SELECT queries are allowed",
    )

if ";" in download_query:
    return self.response(
        400,
        message="Multiple statements not allowed",
    )
