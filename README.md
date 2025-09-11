SELECT 
    "Application_Type",
    "Status",
    COUNT(*) AS "Policy_Count"
FROM "policies"
GROUP BY "Application_Type", "Status"
ORDER BY "Application_Type", "Policy_Count" DESC;
