SELECT
  DATE("Date") AS conversation_date,
  ROUND(
    100.0 * COUNT(CASE WHEN "Amelia Handled" = TRUE AND "Escalated" = FALSE THEN 1 END) 
    / NULLIF(COUNT(*), 0),
    2
  ) AS containment_rate
FROM public."your_table_name"
GROUP BY 1
ORDER BY 1
