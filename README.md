
SELECT
  CAST("Created" AS DATE) AS "Day",
  SUM("count_deflection") AS "SelfAssist",
  SUM("count_deflection_pa_status") AS "Deflected_PA_Status",
  SUM("count_deflection_edit") AS "Deflected_with_Sub.",
  SUM("count_deflection_archive_unarchive") AS "Deflection_Archive"
FROM "your_table"
GROUP BY "Day"
ORDER BY "Day"
