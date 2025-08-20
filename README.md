WITH total AS (
    SELECT COUNT(*)::float AS total_count FROM "New_Republic_Dataset"
),
escalation_summary AS (
    SELECT
        CASE
            WHEN "Escalated" = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN "Escalated" = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
            ELSE 'Not Escalated'
        END AS category,
        COUNT(*)::float AS cnt
    FROM "New_Republic_Dataset"
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
    SELECT category, cnt
    FROM escalation_summary
)
-- Final union for both rings
SELECT category, cnt * 100.0 / t.total_count AS value, 'inner' AS ring
FROM inner_ring, total t
UNION ALL
SELECT category, cnt * 100.0 / t.total_count AS value, 'outer' AS ring
FROM outer_ring, total t;
