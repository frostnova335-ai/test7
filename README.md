try:
    item = self.edit_model_schema.load(request.json)

    if "download_query" in request.json:
        item["download_query"] = request.json.get("download_query")

except ValidationError as error:
    return self.response_400(message=error.messages)
