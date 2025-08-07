SELECT
  ROUND(
    SUM(
      CASE 
        WHEN "Amelia Handled" = TRUE 
             AND "Agent Handled" = FALSE 
             AND "Escalated" = FALSE 
        THEN 1 
        ELSE 0 
      END
    ) * 100.0 / NULLIF(COUNT(*), 0), 
    2
  ) AS "Containment Rate (%)"
FROM public."Republic_dashboard"
WHERE "Amelia Handled" IS NOT NULL;
