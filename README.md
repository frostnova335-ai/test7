SELECT
  CAST("Created" AS DATE) AS "deflection_day",
  SUM(CASE WHEN "self_assist" = 1 THEN 1 ELSE 0 END) AS "Self-Assist",
  SUM(CASE WHEN "deflection_pa_status" = 1 THEN 1 ELSE 0 END) AS "Deflected PA Status",
  SUM(CASE WHEN "deflection_with_subflow" = 1 THEN 1 ELSE 0 END) AS "Deflected With Subflow",
  SUM(CASE WHEN "deflection_archive_unarchive" = 1 THEN 1 ELSE 0 END) AS "Deflection Archive"
FROM "interactions"
GROUP BY "deflection_day"
ORDER BY "deflection_day"
