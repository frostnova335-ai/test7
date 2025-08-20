
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
),
-- Data for the outer ring (3 segments)
outer_ring AS (
    SELECT category, COUNT(*)::float AS cnt
    FROM base
    GROUP BY category
),
-- Data for the inner ring (2 segments: Escalated, Not Escalated)
inner_ring AS (
    SELECT 
        CASE 
            WHEN category = 'Not Escalated' THEN 'Not Escalated'
            ELSE 'Escalated'
        END AS category, 
        COUNT(*)::float AS cnt
    FROM base
    GROUP BY 1
)
-- Final output
SELECT 'outer' AS ring, category, cnt * 100.0 / t.total_count AS value
FROM outer_ring, total t
UNION ALL
SELECT 'inner' AS ring, category, cnt * 100.0 / t.total_count AS value
FROM inner_ring, total t;
