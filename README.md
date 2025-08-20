SELECT
  escalation_status AS escalation_status,
  category AS category,
  SUM("percentage") * 0.01 AS "SUM(""percentage"")*0.01"
FROM (
  WITH base AS (
    SELECT
      "Date" AS "Date",
      CASE
        WHEN "Escalated" = 'In Scope Live Agent Handoff'
        THEN 'In Scope Escalated'
        WHEN "Escalated" = 'Out of Scope Live Agent Handoff'
        THEN 'Out of Scope Escalated'
        ELSE 'Not Escalated'
      END AS category
    FROM "New_Republic_Dataset"
  ), tagged AS (
    SELECT
      "Date",
      CASE
        WHEN category = 'In Scope Escalated' OR category = 'Out of Scope Escalated'
        THEN 'Escalated'
        ELSE 'Not Escalated'
      END AS escalation_status,
      category
    FROM base
  ), aggregated AS (
    SELECT
      "Date",
      escalation_status,
      category,
      COUNT(*) AS count
    FROM tagged
    GROUP BY
      "Date",
      escalation_status,
      category
  ), total AS (
    SELECT
      SUM(count) AS total_count
    FROM aggregated
  )
  SELECT
    a."Date",
    a.escalation_status,
    a.category,
    a.count,
    ROUND(100.0 * a.count / t.total_count, 2) AS percentage
  FROM aggregated AS a, total AS t
  ORDER BY
    a."Date",
    a.count DESC
) AS virtual_table
GROUP BY




  escalation_status,
  category
LIMIT 1000
