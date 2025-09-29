SELECT
  AVG(containment_rate) AS "%"
FROM (
  SELECT
    "Date",
    COUNT(
      CASE
        WHEN "MPU_Case_Closure" = 1
        AND "MPU_Intent_Identified_Flag" = 1
        AND "MPU_Eligible_flag" = 'Eligible'
        THEN 1
      END
    ) * 1.0 / NULLIF(
      COUNT(
        CASE
          WHEN "MPU_Intent_Identified_Flag" = 1 AND "MPU_Eligible_flag" = 'Eligible'
          THEN 1
        END
      ),
      0
    ) AS containment_rate
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
LIMIT 50000








SELECT
  SUM("auth_success_count") / SUM("residential_calls_count") AS "Auth Rate"
FROM (
  SELECT
    DATE("Date") AS "Date",
    SUM(
      CASE
        WHEN "Caller_Type" = 'Residential' AND "Authentication by VA success flag" = 1
        THEN 1
        ELSE 0
      END
    ) AS auth_success_count,
    SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END) AS residential_calls_count,
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Caller_Type" = 'Residential' AND "Authentication by VA success flag" = 1
          THEN 1
          ELSE 0
        END
      ) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0),
      2
    ) AS auth_success_rate
  FROM public."New_Republic_Dataset"
  GROUP BY
    DATE("Date")
  ORDER BY
    DATE("Date")
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
LIMIT 50000






SELECT
  AVG("escalation_rate_percentage") * 0.01 AS "AVG(""escalation_rate_percentage"")*0.01"
FROM (
  SELECT
    "Date",
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Caller_Type" = 'Residential'
          AND "Escalated" IN ('Out of Scope Live Agent Handoff', 'In Scope Live Agent Handoff')
          THEN 1
          ELSE 0
        END
      ) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0),
      2
    ) AS escalation_rate_percentage
  FROM public."New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
WHERE
  "Date" >= '2025-08-29 00:00:00.000000' AND "Date" < '2025-09-29 00:00:00.000000'
LIMIT 50000





SELECT
  AVG("abandonment_rate") * 0.01 AS "AVG(""abandonment_rate"")*0.01"
FROM (
  SELECT
    'Abandonment' AS label,
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Abandonment by customer - flag" = 1
          AND "Abandoned_during_VA" = 1
          AND "MPU_Case_Closure" IS DISTINCT FROM '1'
          THEN 1
          ELSE 0
        END
      ) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0),
      2
    ) AS abandonment_rate
  FROM public."New_Republic_Dataset"
) AS virtual_table
LIMIT 50000






SELECT
  AVG("missed_utterance_rate") * 0.01 AS "%"
FROM (
  SELECT
    "Date",
    (
      CAST(SUM("Missed_Utterance") AS DOUBLE PRECISION) / NULLIF(SUM("Number of Prompts from AI"), 0)
    ) * 100 AS missed_utterance_rate
  FROM public."New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
LIMIT 50000









SELECT
  ROUND(SUM("handle_time") / SUM("count_conv")) AS "AHT"
FROM (
  SELECT
    DATE("Date") AS "Date",
    'AHT' AS "Metric",
    SUM("AHT") AS handle_time,
    COUNT("Conversation Id") AS Count_conv
  FROM public."New_Republic_Dataset"
  WHERE
    "Caller_Type" = 'Residential' AND NOT "AHT" IS NULL
  GROUP BY
    DATE("Date")
  ORDER BY
    DATE("Date")
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
LIMIT 50000









SELECT
  "Date" AS "Date",
  SUM(containment_rate) AS "%"
FROM (
  SELECT
    "Date",
    COUNT(
      CASE
        WHEN "MPU_Case_Closure" = 1
        AND "MPU_Intent_Identified_Flag" = 1
        AND "MPU_Eligible_flag" = 'Eligible'
        THEN 1
      END
    ) * 1.0 / NULLIF(
      COUNT(
        CASE
          WHEN "MPU_Intent_Identified_Flag" = 1 AND "MPU_Eligible_flag" = 'Eligible'
          THEN 1
        END
      ),
      0
    ) AS containment_rate
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
GROUP BY
  "Date"
ORDER BY
  "%" DESC
LIMIT 10000









SELECT
  DATE_TRUNC('DAY', "Date") AS "Date",
  SUM("auth_success_rate") * 0.01 AS "SUM(""auth_success_rate"")*0.01"
FROM (
  SELECT
    "Date",
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Caller_Type" = 'Residential' AND "Authentication by VA success flag" = 1
          THEN 1
          ELSE 0
        END
      ) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0),
      2
    ) AS auth_success_rate
  FROM public."New_Republic_Dataset"
  GROUP BY
    "Date"
) AS virtual_table
WHERE
  "Date" >= '2025-08-29 00:00:00.000000' AND "Date" < '2025-09-29 00:00:00.000000'
GROUP BY
  DATE_TRUNC('DAY', "Date")
ORDER BY
  "SUM(""auth_success_rate"")*0.01" DESC
LIMIT 1000








SELECT
  "MPU_Retry_Prompt" AS "MPU_Retry_Prompt",
  SUM(retry_count) AS "Volume"
FROM (
  SELECT
    DATE("Date") AS "Date",
    "MPU_Retry_Prompt",
    COUNT(*) AS retry_count
  FROM public."New_Republic_Dataset"
  WHERE
    "Retry of MPU flag" = 1 AND "Caller_Type" = 'Residential'
  GROUP BY
    DATE("Date"),
    "MPU_Retry_Prompt"
  ORDER BY
    retry_count DESC
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
GROUP BY
  "MPU_Retry_Prompt"
ORDER BY
  "Volume" DESC
LIMIT 1000

SELECT
  DATE_TRUNC('DAY', "Date") AS "Date",
  AVG("escalation_rate") AS "Rate"
FROM (
  SELECT
    DATE("Date") AS "Date",
    CAST(SUM(
      CASE
        WHEN "Caller_Type" = 'Residential'
        AND "Escalated" IN ('Out of Scope Live Agent Handoff', 'In Scope Live Agent Handoff')
        THEN 1
        ELSE 0
      END
    ) /* Rate as a decimal (0.05 = 5%) */ AS DECIMAL) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0) AS escalation_rate,
    SUM(
      CASE
        WHEN "Caller_Type" = 'Residential'
        AND "Escalated" IN ('Out of Scope Live Agent Handoff', 'In Scope Live Agent Handoff')
        THEN 1
        ELSE 0
      END
    ) AS escalation_volume /* Absolute volume */
  FROM public."New_Republic_Dataset"
  GROUP BY
    DATE("Date")
  ORDER BY
    DATE("Date")
) AS virtual_table
GROUP BY
  DATE_TRUNC('DAY', "Date")
ORDER BY
  "Rate" DESC
LIMIT 1000



SELECT
  label AS label,
  AVG("abandonment_rate") * 0.01 AS "Rate"
FROM (
  SELECT
    'Abandonment' AS label,
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Abandonment by customer - flag" = 1
          AND "Abandoned_during_VA" = 1
          AND "MPU_Case_Closure" IS DISTINCT FROM '1'
          THEN 1
          ELSE 0
        END
      ) / NULLIF(SUM(CASE WHEN "Caller_Type" = 'Residential' THEN 1 ELSE 0 END), 0),
      2
    ) AS abandonment_rate
  FROM public."New_Republic_Dataset"
) AS virtual_table
GROUP BY
  label
ORDER BY
  "Rate" DESC
LIMIT 1000



SELECT
  DATE_TRUNC('DAY', "Date") AS "Date",
  SUM(out_of_scope_rate) AS "%"
FROM (
  SELECT
    "Date",
    COUNT(
      CASE
        WHEN "Caller_Type" = 'Residential'
        AND "Authentication by VA success flag" = 1
        AND "MPU_Intent_Identified_Flag" = 0
        THEN 1
      END
    ) * 1.0 / NULLIF(
      COUNT(
        CASE
          WHEN "Caller_Type" = 'Residential' AND "Authentication by VA success flag" = 1
          THEN 1
        END
      ),
      0
    ) AS out_of_scope_rate
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
WHERE
  "Date" >= '2025-08-29 00:00:00.000000' AND "Date" < '2025-09-29 00:00:00.000000'
GROUP BY
  DATE_TRUNC('DAY', "Date")
ORDER BY
  "%" DESC
LIMIT 1000


SELECT
  DATE_TRUNC('DAY', "Date") AS "Date",
  SUM(out_of_scope_rate_2) AS "%"
FROM (
  SELECT
    "Date",
    COUNT(
      CASE
        WHEN "Caller_Type" = 'Residential'
        AND "Authentication by VA success flag" = 1
        AND "MPU_Intent_Identified_Flag" = 1
        AND "Here_for_MPU_Flag" = 0
        THEN 1
      END
    ) * 1.0 / NULLIF(
      COUNT(
        CASE
          WHEN "Caller_Type" = 'Residential'
          AND "Authentication by VA success flag" = 1
          AND "MPU_Intent_Identified_Flag" = 1
          THEN 1
        END
      ),
      0
    ) AS out_of_scope_rate_2
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
GROUP BY
  DATE_TRUNC('DAY', "Date")
ORDER BY
  "%" DESC
LIMIT 1000



SELECT
  "Date" AS "Date",
  SUM(intent_success_rate) AS "%"
FROM (
  SELECT
    "Date",
    COUNT(
      CASE
        WHEN "MPU_Intent_Identified_1stattempt_Flag" = 1
        AND "Here_for_MPU_Flag" = 1
        AND "Caller_Type" = 'Residential'
        AND "Authentication by VA success flag" = 1
        AND "MPU_Intent_Identified_Flag" = 1
        THEN 1
      END
    ) * 1.0 / NULLIF(
      COUNT(
        CASE
          WHEN "Caller_Type" = 'Residential'
          AND "Authentication by VA success flag" = 1
          AND "MPU_Intent_Identified_Flag" = 1
          THEN 1
        END
      ),
      0
    ) AS intent_success_rate
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
  ORDER BY
    "Date"
) AS virtual_table
GROUP BY
  "Date"
ORDER BY
  "%" DESC
LIMIT 1000



SELECT
  "Date" AS "Date",
  SUM("success_rate") * 0.01 AS "SUM(""success_rate"")*0.01"
FROM (
  SELECT
    "Date",
    SUM("Number of Successful Prompts from AI") * 100.0 / NULLIF(SUM("Number of Prompts from AI"), 0) AS success_rate
  FROM "New_Republic_Dataset"
  GROUP BY
    "Date"
) AS virtual_table
WHERE
  "Date" >= TO_TIMESTAMP('2025-08-29 00:00:00.000000', 'YYYY-MM-DD HH24:MI:SS.US')
  AND "Date" < TO_TIMESTAMP('2025-09-29 00:00:00.000000', 'YYYY-MM-DD HH24:MI:SS.US')
GROUP BY
  "Date"
ORDER BY
  "SUM(""success_rate"")*0.01" DESC
LIMIT 1000


SELECT
  category AS category,
  AVG(value) AS "Rate"
FROM (
  WITH base AS (
    SELECT
      "Date",
      CAST(SUM("Missed_Utterance") AS DOUBLE PRECISION) AS missed,
      CAST(SUM("Number of Prompts from AI") AS DOUBLE PRECISION) AS total_prompts
    FROM public."New_Republic_Dataset"
    GROUP BY
      "Date"
  )
  SELECT
    "Date",
    'Missed Utterance' AS "category",
    (
      missed / NULLIF(total_prompts, 0)
    ) * 100 AS "value"
  FROM base
  UNION ALL
  SELECT
    "Date",
    'Rest' AS "category", /* Changed here */
    (
      (
        total_prompts - missed
      ) / NULLIF(total_prompts, 0)
    ) * 100 AS "value"
  FROM base
  ORDER BY
    "Date",
    "category"
) AS virtual_table
GROUP BY
  category
ORDER BY
  "Rate" DESC
LIMIT 100



SELECT
  "Date" AS "Date",
  AVG("angelic_handled") * 0.01 AS "AVG(""angelic_handled"")*0.01"
FROM (
  SELECT
    "Date",
    'AI Traffic Share' AS "AI Traffic Share",
    ROUND(
      100.0 * SUM(CASE WHEN "Handled by Agentic AI flag" = 1 THEN 1 ELSE 0 END) / COUNT(CASE WHEN "Caller_Type" = 'Residential' THEN 1 END),
      2
    ) AS Angelic_handled
  FROM public."New_Republic_Dataset"
  WHERE
    "Caller_Type" = 'Residential'
  GROUP BY
    "Date"
) AS virtual_table
GROUP BY
  "Date"
ORDER BY
  "AVG(""angelic_handled"")*0.01" DESC
LIMIT 1000


SELECT
  "Half_hourly_interval" AS "Half_hourly_interval",
  AVG(avg_contacts_per_active_day) AS "Total Volume ",
  AVG(avg_escalated_per_active_day) AS "Live Agent Handoff Volume"
FROM (
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
) AS virtual_table
WHERE
  "Date" >= TO_TIMESTAMP('2025-08-29 00:00:00.000000', 'YYYY-MM-DD HH24:MI:SS.US')
  AND "Date" < TO_TIMESTAMP('2025-09-29 00:00:00.000000', 'YYYY-MM-DD HH24:MI:SS.US')
GROUP BY
  "Half_hourly_interval"
ORDER BY
  "Total Volume " DESC
LIMIT 1000



SELECT
  "Metric" AS "Metric",
  ROUND(SUM("handle_time") / SUM("count_conv")) AS "AHT"
FROM (
  SELECT
    DATE("Date") AS "Date",
    'AHT' AS "Metric",
    SUM("AHT") AS handle_time,
    COUNT("Conversation Id") AS Count_conv
  FROM public."New_Republic_Dataset"
  WHERE
    "Caller_Type" = 'Residential' AND NOT "AHT" IS NULL
  GROUP BY
    DATE("Date")
  ORDER BY
    DATE("Date")
) AS virtual_table
GROUP BY
  "Metric"
ORDER BY
  "AHT" DESC
LIMIT 1000
