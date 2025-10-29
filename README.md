WITH daily_counts AS (
    SELECT
      "Date",
      "Half_hourly_interval",
      COUNT(*) AS total_contacts,
      COUNT(
        CASE
          WHEN "Escalated" IN ('Out of Scope Live Agent Handoff', 'In Scope Live Agent Handoff')
          THEN 1
        END
      ) AS escalated_contacts
    FROM public."New_Republic_Dataset"
    GROUP BY
      "Date",
      "Half_hourly_interval"
  ), interval_totals AS (
    SELECT
      "Date",
      "Half_hourly_interval",
      SUM(total_contacts) AS sum_contacts,
      SUM(escalated_contacts) AS sum_escalated,
      COUNT(*) AS active_days
    FROM daily_counts
    WHERE
      total_contacts > 0
    GROUP BY
      "Date",
      "Half_hourly_interval"
  )
  SELECT
    "Date",
    it."Half_hourly_interval",
    CAST(it.sum_contacts AS DOUBLE PRECISION) / NULLIF(it.active_days, 0) AS avg_contacts_per_active_day,
    CAST(it.sum_escalated AS DOUBLE PRECISION) / NULLIF(it.active_days, 0) AS avg_escalated_per_active_day
  FROM interval_totals AS it
  ORDER BY
    "Date",
    it."Half_hourly_interval"
