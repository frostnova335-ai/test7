SELECT
  DATE("Created") AS "date",
  ROUND(
    100.0 * SUM(
      CASE
        WHEN "Amelia Handled" = TRUE AND "Escalated" = FALSE THEN 1
        ELSE 0
      END
    ) / COUNT(*),
    2
  ) AS "containment_rate"
FROM public."Republic_dashboard"
GROUP BY DATE("Created")
ORDER BY DATE("Created");
