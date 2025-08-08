SELECT
  DATE("Date") AS conversation_date,
  ROUND(
    100.0 * SUM(CASE WHEN "Authentication by VA success flag" = 1 THEN 1 ELSE 0 END)
    / NULLIF(COUNT(*), 0),
    2
  ) AS auth_success_rate
FROM public."your_table_name"
GROUP BY 1
ORDER BY 1
