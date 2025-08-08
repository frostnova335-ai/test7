SELECT
  'Abandonment' AS metric_label,
  ROUND(
    100.0 * COUNT(CASE 
                   WHEN "Abandonment by customer - flag" = 1 THEN 1 
                 END)
    / NULLIF(COUNT(*), 0),
    2
  ) AS abandonment_rate
FROM public."your_table_name"
