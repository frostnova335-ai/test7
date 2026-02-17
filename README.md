Abondonment stage query 

WITH total_calls AS (
    SELECT
      COUNT(*) AS total_call_count
    FROM public."adtnew"
    WHERE
      "Caller_Type" = 'Residential'
  ), abandonment_by_stage AS (
    SELECT
      TRIM("Abandonment_Last_Completed_Stage") AS journey_step,
      COUNT(*) AS abandoned_count
    FROM public."adtnew"
    WHERE
      "Abandonment by customer - flag" = 1
      AND "Abandoned_during_VA" = 1
      AND "Caller_Type" = 'Residential'
      AND NOT "Abandonment_Last_Completed_Stage" IS NULL
      AND TRIM("Abandonment_Last_Completed_Stage") <> ''
    GROUP BY
      TRIM("Abandonment_Last_Completed_Stage")
  )
  SELECT
    abs.journey_step,
    abs.abandoned_count,
    ROUND(100.0 * abs.abandoned_count / tc.total_call_count, 2) AS abandonment_rate_pct
  FROM abandonment_by_stage AS abs
  CROSS JOIN total_calls AS tc
  ORDER BY
    abandonment_rate_pct DESC



	traffic handled by ai query also in this used date at cte level so that no impact on output but filter can be used 


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
