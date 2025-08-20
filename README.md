WITH base AS (
    SELECT
        CASE
            WHEN "Escalated" = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN "Escalated" = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
            ELSE 'Not Escalated'
        END AS category
    FROM "New_Republic_Dataset"
), 
total AS (
    SELECT COUNT(*)::float AS total_count FROM base
)
SELECT
    category,
    COUNT(*) * 100.0 / (SELECT total_count FROM total) AS percentage
FROM base
GROUP BY category;
