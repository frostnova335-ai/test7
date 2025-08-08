SELECT 
  DATE("created") AS date,
  'Abandonment Rate' AS abandonment_category,
  ROUND(
    SUM(
      CASE 
        WHEN abandonment_by_customer_flag = 1 OR amelia_abandonment_flag = 1 THEN 1 
        ELSE 0 
      END
    ) * 100.0 / COUNT(*),
  2) AS abandonment_rate_percent
FROM public."your_table"
GROUP BY DATE("created")
ORDER BY DATE("created");
