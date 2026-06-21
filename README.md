try:
    result = db.session.execute(
        text(download_query)
    )
except Exception as ex:
    return self.response(
        400,
        message=str(ex),
    )
