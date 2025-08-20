WITH total AS (
    SELECT COUNT(*)::float AS total_count FROM your_table
),
escalation_summary AS (
    SELECT
        CASE
            WHEN Escalated = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN Escalated = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
            ELSE 'Not Escalated'
        END AS category,
        COUNT(*)::float AS cnt
    FROM your_table
    GROUP BY 1
),
inner_ring AS (
    SELECT 
        CASE 
            WHEN category = 'Not Escalated' THEN 'Not Escalated'
            ELSE 'Escalated'
        END AS category,
        SUM(cnt) AS cnt
    FROM escalation_summary
    GROUP BY 1
),
outer_ring AS (
    -- keep "Not Escalated" only once, along with the two breakdowns
    SELECT category, cnt
    FROM escalation_summary
)
-- Final union for both rings
SELECT category, cnt * 100.0 / t.total_count AS value, 'inner' AS ring
FROM inner_ring, total t
UNION ALL
SELECT category, cnt * 100.0 / t.total_count AS value, 'outer' AS ring
FROM outer_ring, total t
WHERE category IN ('In Scope Escalated', 'Out of Scope Escalated', 'Not Escalated');
