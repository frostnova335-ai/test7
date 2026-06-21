result = self.dashboard_get_response_schema.dump(dash)

metadata = json.loads(dash.json_metadata or "{}")

result["download_query"] = metadata.get("download_query")
