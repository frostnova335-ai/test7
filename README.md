download_query = self._properties.pop(
    "download_query",
    None,
)

if download_query is not None:
    metadata = json.loads(self._model.json_metadata or "{}")
    metadata["download_query"] = download_query

    self._properties["json_metadata"] = json.dumps(metadata)
