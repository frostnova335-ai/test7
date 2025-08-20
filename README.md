WITH total_calls AS (
    SELECT COUNT(*) AS total FROM your_table
),
escalated_calls AS (
    SELECT COUNT(*) AS escalated
    FROM your_table
    WHERE Escalated != 'FALSE'
),
non_escalated_calls AS (
    SELECT COUNT(*) AS not_escalated
    FROM your_table
    WHERE Escalated = 'FALSE'
),
escalation_breakdown AS (
    SELECT Escalated, COUNT(*) AS count
    FROM your_table
    WHERE Escalated != 'FALSE'
    GROUP BY Escalated
)
-- Final output for both rings
SELECT 
    'Escalated' AS category, e.escalated AS value, 'inner' AS ring
FROM escalated_calls e
UNION ALL
SELECT 
    'Not Escalated' AS category, n.not_escalated AS value, 'inner' AS ring
FROM non_escalated_calls n
UNION ALL
SELECT 
    Escalated AS category, count AS value, 'outer' AS ring
FROM escalation_breakdown;

