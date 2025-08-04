
SELECT
  "day",
  'Billed Interactions' AS label,
  COUNT(DISTINCT "Conversation Id") AS value
FROM (
  SELECT 
    DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
    "Conversation Id",
    "Amelia Abandoned",
    "Amelia Category",
    "count_deflection_edit",
    "count_deflection_archive_unarchive"
  FROM public."Mckesson_cmm_va"
  WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
) base
WHERE 
  (
    ("Amelia Abandoned" = 'True' AND "Amelia Category" = 'PA Status')
    OR ("count_deflection_edit" = 1)
    OR ("count_deflection_archive_unarchive" = 1)
  )
GROUP BY 1

UNION ALL

SELECT
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'Billed PA Status' AS label,
  COUNT(DISTINCT "Conversation Id") AS value
FROM public."Mckesson_cmm_va"
WHERE 
  "Amelia Abandoned" = 'True'
  AND "Amelia Category" = 'PA Status'
  AND TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

UNION ALL

SELECT
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'Deflection Edit' AS label,
  SUM(CASE WHEN "count_deflection_edit" = 1 THEN 1 ELSE 0 END) AS value
FROM public."Mckesson_cmm_va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

UNION ALL

SELECT
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'Deflection Archive/Unarchive' AS label,
  SUM(CASE WHEN "count_deflection_archive_unarchive" = 1 THEN 1 ELSE 0 END) AS value
FROM public."Mckesson_cmm_va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

ORDER BY "day", label;
