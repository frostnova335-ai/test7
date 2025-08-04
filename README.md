
SELECT
  DATE("created") AS date,
  COUNT(*) AS billed_interactions,
  SUM("count_testrequest") AS billed_ps_status,
  SUM("count_deflection_edit") AS deflection_edit,
  SUM("count_deflection_archive_unarchive") AS deflection_archive
FROM public."Mckesson_cmm_va"
WHERE "created" BETWEEN DATE '2025-03-01' AND DATE '2025-05-06'
GROUP BY date
ORDER BY date;
