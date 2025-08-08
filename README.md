SELECT
  DATE("created") AS date,
  SUM("successful_prompts") * 100.0 / NULLIF(SUM("total_prompts"), 0) AS success_rate
FROM "Republic_dashboard"
GROUP BY DATE("created")
ORDER BY DATE("created")
