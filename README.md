SELECT 
  DATE("date_column") AS date,
  'Abandonment Rate' AS abandonment_category,
  ROUND(
    (
      SUM(CASE WHEN abandonment_by_customer_flag = 1 THEN 1 ELSE 0 END) + 
      SUM(CASE WHEN amelia_abandonment_flag = 1 THEN 1 ELSE 0 END)
    ) * 100.0 / COUNT(*),
  2) AS abandonment_rate_percent
FROM public."your_table"
GROUP BY DATE("date_column")
ORDER BY DATE("date_column")
