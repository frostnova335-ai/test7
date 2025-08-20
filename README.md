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
    SELECT COUNT(*)::numeric AS total_count FROM base
),
-- Inner ring = Escalated vs Not Escalated
inner_ring AS (
    SELECT
        CASE 
            WHEN category = 'Not Escalated' THEN 'Not Escalated'
            ELSE 'Escalated'
        END AS category,
        COUNT(*)::numeric AS cnt
    FROM base
    GROUP BY 1
),
-- Outer ring = only the 3 categories (no "Escalated")
outer_ring AS (
    SELECT category, COUNT(*)::numeric AS cnt
    FROM base
    GROUP BY 1
    HAVING category IN ('Not Escalated', 'In Scope Escalated', 'Out of Scope Escalated')
)
-- Final output
SELECT 
    category, 
    ROUND((cnt * 100.0 / t.total_count)::numeric, 2) AS percentage, 
    'inner' AS ring
FROM inner_ring, total t
UNION ALL
SELECT 
    category, 
    ROUND((cnt * 100.0 / t.total_count)::numeric, 2) AS percentage, 
    'outer' AS ring
FROM outer_ring, total t;
