WITH base AS (
    SELECT
        CASE
            WHEN "Escalated" = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN "Escalated" = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
            ELSE 'Not Escalated'
        END AS outer_category
    FROM "New_Republic_Dataset"
),
total AS (
    SELECT COUNT(*)::float AS total_count FROM base
)
-- Outer ring
SELECT 
    'outer' AS ring,
    outer_category AS category,
    COUNT(*) * 100.0 / (SELECT total_count FROM total) AS value
FROM base
GROUP BY outer_category
UNION ALL
-- Middle ring: Classify as 'Escalated' if either outer category is escalated, else 'Not Escalated'
SELECT 
    'middle' AS ring,
    CASE WHEN outer_category = 'Not Escalated' THEN 'Not Escalated' ELSE 'Escalated' END AS category,
    COUNT(*) * 100.0 / (SELECT total_count FROM total) AS value
FROM base
GROUP BY CASE WHEN outer_category = 'Not Escalated' THEN 'Not Escalated' ELSE 'Escalated' END
UNION ALL
-- Inner ring: sum for overall 'Not Escalated' and 'Escalated'
SELECT 
    'inner' AS ring,
    'Not Escalated' AS category,
    SUM(CASE WHEN outer_category = 'Not Escalated' THEN 1 ELSE 0 END) * 100.0 / (SELECT total_count FROM total) AS value
FROM base
UNION ALL
SELECT 
    'inner' AS ring,
    'Escalated' AS category,
    SUM(CASE WHEN outer_category IN ('In Scope Escalated', 'Out of Scope Escalated') THEN 1 ELSE 0 END) * 100.0 / (SELECT total_count FROM total) AS value
FROM base;
