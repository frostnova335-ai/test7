SELECT
  DATE("Date") AS conversation_date,
  ROUND(
    100.0 * SUM(CASE WHEN "Intent recognition success by VA flag" = 1 THEN 1 ELSE 0 END)
    / NULLIF(COUNT(*), 0),
    2
  ) AS intent_recognition_rate
FROM public."your_table_name"
GROUP BY 1
ORDER BY 1
