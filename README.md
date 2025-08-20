WITH "total_calls" AS (
    SELECT COUNT(*) AS "total"
    FROM "New_Republic_Dataset"
),
"escalated_calls" AS (
    SELECT COUNT(*) AS "escalated"
    FROM "New_Republic_Dataset"
    WHERE "Escalated" != 'FALSE'
),
"non_escalated_calls" AS (
    SELECT COUNT(*) AS "not_escalated"
    FROM "New_Republic_Dataset"
    WHERE "Escalated" = 'FALSE'
),
-- Breakdown of escalations (only those that are escalated)
"escalation_breakdown" AS (
    SELECT 
        CASE 
            WHEN "Escalated" = 'In Scope Live Agent Handoff' THEN 'In Scope Escalated'
            WHEN "Escalated" = 'Out of Scope Live Agent Handoff' THEN 'Out of Scope Escalated'
        END AS "Escalation_Type",
        COUNT(*) AS "count"
    FROM "New_Republic_Dataset"
    WHERE "Escalated" != 'FALSE'
    GROUP BY 1
)
-- Final Output with percentages
SELECT 
    'Escalated' AS "category",
    ROUND(100.0 * e."escalated" / t."total", 2) AS "value",
    'inner' AS "ring"
FROM "escalated_calls" e, "total_calls" t

UNION ALL

SELECT 
    'Not Escalated' AS "category",
    ROUND(100.0 * n."not_escalated" / t."total", 2) AS "value",
    'inner' AS "ring"
FROM "non_escalated_calls" n, "total_calls" t

UNION ALL

SELECT 
    "Escalation_Type" AS "category",
    ROUND(100.0 * b."count" / t."total", 2) AS "value",
    'outer' AS "ring"
FROM "escalation_breakdown" b, "total_calls" t

UNION ALL

-- Not Escalated also needs to appear in the outer ring
SELECT 
    'Not Escalated' AS "category",
    ROUND(100.0 * n."not_escalated" / t."total", 2) AS "value",
    'outer' AS "ring"
FROM "non_escalated_calls" n, "total_calls" t;
