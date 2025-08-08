SELECT
  DATE("date") AS date,
  'World AHT' AS "World AHT",
  ROUND(AVG("AHT"), 2) AS avg_handle_time
FROM public."Republic_dashboard"
GROUP BY DATE("date")
ORDER BY DATE("date")
