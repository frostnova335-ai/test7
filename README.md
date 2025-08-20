SELECT
  escalation_status AS escalation_status,
  category AS category,
  SUM("percentage") * 0.01 AS "Rate"
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
      category,
      CASE WHEN category = 'Not Escalated' THEN 1 ELSE 2 END AS sort_order
    FROM base
  ), aggregated AS (
    SELECT
      "Date",
      escalation_status,
      category,
      COUNT(*) AS count,
      MIN(sort_order) AS sort_order
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
    a.sort_order,
    ROUND(100.0 * a.count / t.total_count, 2) AS percentage
  FROM aggregated AS a, total AS t
  ORDER BY
    a."Date",
    a.sort_order,
    a.count DESC
) AS virtual_table
GROUP BY
  escalation_status,
  category
LIMIT 1000










SELECT
  auth_stage_group AS auth_stage_group,
  auth_stage_detail AS auth_stage_detail,
  SUM("percentage") * 0.01 AS "Rate"
FROM (
  WITH filtered_data AS (
    SELECT
      "Date" AS "Date",
      'Out of Scope' AS escalation_type,
      CASE
        WHEN "Escalated_2" = 'During Authentication'
        THEN 'During Authentication'
        ELSE 'After Authentication'
      END AS auth_stage_group,
      "Escalated_2" AS auth_stage_detail
    FROM public."New_Republic_Dataset"
    WHERE
      "Escalated" = 'Out of Scope Live Agent Handoff'
      AND "Escalated_2" IN (
        'During Authentication',
        'After Authentication (MPU Only)',
        'After Authentication (MPU + Others)',
        'After Authentication (Others)'
      )
  ), grouped AS (
    SELECT
      "Date",
      auth_stage_group,
      auth_stage_detail,
      COUNT(*) AS count
    FROM filtered_data
    GROUP BY
      "Date",
      auth_stage_group,
      auth_stage_detail
  ), total AS (
    SELECT
      SUM(count) AS total_count
    FROM grouped
  )
  SELECT
    g."Date",
    g.auth_stage_group,
    g.auth_stage_detail,
    g.count,
    ROUND(100.0 * g.count / t.total_count, 2) AS percentage
  FROM grouped AS g, total AS t
  ORDER BY
    g."Date",
    g.auth_stage_group,
    g.auth_stage_detail
) AS virtual_table
GROUP BY
  auth_stage_group,
  auth_stage_detail
LIMIT 1000
