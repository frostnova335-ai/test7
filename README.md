WITH base AS (
    SELECT
        CASE
            WHEN "Escalated" = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN "Escalated" = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
            ELSE 'Not Escalated'
        END AS category
    FROM "New_Republic_Dataset"
),
outer_ring AS (
    SELECT 'outer' AS ring, category, COUNT(*) AS value
    FROM base
    WHERE category IN ('Not Escalated', 'In Scope Escalated', 'Out of Scope Escalated')
    GROUP BY category
),
inner_ring AS (
    SELECT 'inner' AS ring, 'Escalated' AS category,
        COUNT(*) AS value
    FROM base
    WHERE category IN ('In Scope Escalated', 'Out of Scope Escalated')
    UNION ALL
    SELECT 'inner' AS ring, 'Not Escalated' AS category,
        COUNT(*) AS value
    FROM base
    WHERE category = 'Not Escalated'
)
SELECT ring, category, value
FROM outer_ring
UNION ALL
SELECT ring, category, value
FROM inner_ring;
