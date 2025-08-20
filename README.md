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
    SELECT category, COUNT(*)::float AS cnt
    FROM base
    WHERE category IN ('Not Escalated', 'In Scope Escalated', 'Out of Scope Escalated')
    GROUP BY category
),
inner_ring AS (
    SELECT 'Escalated' AS category, COUNT(*)::float AS cnt
    FROM base
    WHERE category IN ('In Scope Escalated', 'Out of Scope Escalated')
    UNION ALL
    SELECT 'Not Escalated' AS category, COUNT(*)::float AS cnt
    FROM base
    WHERE category = 'Not Escalated'
)
SELECT 'outer' AS ring, category, cnt * 100.0 / t.total_count AS value
FROM outer_ring, total t
UNION ALL
SELECT 'inner' AS ring, category, cnt * 100.0 / t.total_count AS value
FROM inner_ring, total t;
