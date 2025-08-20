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
outer_ring AS (
    -- Only 3 categories
    SELECT category, COUNT(*)::float AS cnt
    FROM base
    GROUP BY 1
),
inner_ring AS (
    -- Escalated vs Not Escalated
    SELECT
        CASE 
            WHEN category = 'Not Escalated' THEN 'Not Escalated'
            ELSE 'Escalated'
        END AS category,
        COUNT(*)::float AS cnt
    FROM base
    GROUP BY 1
)
-- Final output for sunburst chart
SELECT category, cnt * 100.0 / t.total_count AS value, 'inner' AS ring
FROM inner_ring, total t
UNION ALL
SELECT category, cnt * 100.0 / t.total_count AS value, 'outer' AS ring
FROM outer_ring, total t;
