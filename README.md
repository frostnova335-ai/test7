SELECT
  "Auth_Retry_Prompt" AS "Auth_Retry_Prompt",
  SUM(retry_count) AS "Volume"
FROM (
  SELECT
    DATE("Date") AS "Date",
    "Auth_Retry_Prompt",
    COUNT(*) AS retry_count
  FROM public."New_Republic_Dataset"
  WHERE
    "Retry of authentication flag" = 1 AND "Caller_Type" = 'Residential'
  GROUP BY
    DATE("Date"),
    "Auth_Retry_Prompt"
  ORDER BY
    retry_count DESC
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
GROUP BY
  "Auth_Retry_Prompt"
ORDER BY
  "Volume" DESC
LIMIT 1000



SELECT
  "Escalation_Type" AS "Escalation_Type",
  SUM("Count") AS "Percentage"
FROM (
  WITH residential_calls AS (
    SELECT
      "Date",
      CASE
        WHEN "Escalated" = 'In Scope Live Agent Handoff'
        THEN 'In Scope'
        WHEN "Escalated" = 'Out of Scope Live Agent Handoff'
        THEN 'Out of Scope'
        ELSE 'Other'
      END AS "Escalation_Type"
    FROM public."New_Republic_Dataset"
    WHERE
      "Caller_Type" = 'Residential'
  )
  SELECT
    "Date",
    "Escalation_Type",
    COUNT(*) AS "Count",
    ROUND(COUNT(*) * 100.0 / NULLIF(SUM(COUNT(*)) OVER (PARTITION BY "Date"), 0), 2) AS "Percentage"
  FROM residential_calls
  GROUP BY
    "Date",
    "Escalation_Type"
  ORDER BY
    "Date",
    "Escalation_Type"
) AS virtual_table
WHERE
  (
    NOT "Escalation_Type" IN ('Other')
  )
GROUP BY
  "Escalation_Type"
ORDER BY
  "Percentage" DESC
LIMIT 100


SELECT
  "Escalated_2" AS "Escalated_2",
  SUM("Count") AS "Percentage"
FROM (
  WITH out_of_scope_totals AS (
    SELECT
      "Date",
      COUNT(*) AS total_out_of_scope
    FROM public."New_Republic_Dataset"
    WHERE
      "Escalated" = 'Out of Scope Live Agent Handoff' AND "Caller_Type" = 'Residential'
    GROUP BY
      "Date"
  )
  SELECT
    d."Date",
    d."Escalated_2",
    COUNT(*) AS "Count",
    ROUND(COUNT(*) * 100.0 / t.total_out_of_scope, 2) AS "Percentage"
  FROM public."New_Republic_Dataset" AS d
  JOIN out_of_scope_totals AS t
    ON d."Date" = t."Date"
  WHERE
    d."Escalated" = 'Out of Scope Live Agent Handoff'
    AND d."Caller_Type" = 'Residential'
  GROUP BY
    d."Date",
    d."Escalated_2",
    t.total_out_of_scope
  ORDER BY
    d."Date",
    d."Escalated_2"
) AS virtual_table
GROUP BY
  "Escalated_2"
ORDER BY
  "Percentage" DESC
LIMIT 100


SELECT
  journey_step AS journey_step,
  AVG("abandonment_rate_pct") * 0.01 AS "Rate"
FROM (
  WITH total_calls AS (
    SELECT
      COUNT(*) AS total_call_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Caller_Type" = 'Residential'
  ), abandonment_by_stage AS (
    SELECT
      TRIM("Abandonment_Last_Completed_Stage") AS journey_step,
      COUNT(*) AS abandoned_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Abandonment by customer - flag" = 1
      AND "Abandoned_during_VA" = 1
      AND (
        "MPU_Case_Closure" IS DISTINCT FROM '1'
      ) /* <-- exclude only '1' */
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
) AS virtual_table
GROUP BY
  journey_step
ORDER BY
  "Rate" DESC
LIMIT 1000


SELECT
  conversation_length AS conversation_length,
  AVG("abandonment_rate_pct") * 0.01 AS "Rate"
FROM (
  WITH total_calls AS (
    SELECT
      COUNT(*) AS total_calls
    FROM public."New_Republic_Dataset"
    WHERE
      "Caller_Type" = 'Residential'
  )
  SELECT
    "AHT_Bucket" AS conversation_length,
    ROUND(
      100.0 * SUM(
        CASE
          WHEN "Abandonment by customer - flag" = 1
          AND "Abandoned_during_VA" = 1
          AND "MPU_Case_Closure" IS DISTINCT FROM '1'
          THEN 1
          ELSE 0
        END
      ) / total_calls.total_calls,
      2
    ) AS abandonment_rate_pct
  FROM public."New_Republic_Dataset", total_calls
  WHERE
    NOT "AHT_Bucket" IS NULL AND "Caller_Type" = 'Residential'
  GROUP BY
    "AHT_Bucket",
    total_calls.total_calls
  ORDER BY
    abandonment_rate_pct DESC
) AS virtual_table
GROUP BY
  conversation_length
ORDER BY
  "Rate" DESC
LIMIT 1000



SELECT
  kpi_name AS kpi_name,
  AVG(kpi_value) AS "Rate"
FROM (
  WITH auth AS (
    SELECT
      "Date",
      'Authentication' AS "kpi_name",
      CAST(SUM("Missed_Utterance_Auth") AS DOUBLE PRECISION) / NULLIF(SUM("AI_Prompts_Auth"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY
      "Date"
  ), intent_id AS (
    SELECT
      "Date",
      'Intent Identification' AS "kpi_name",
      CAST(SUM("Missed_Utterance_IntentIdentification") AS DOUBLE PRECISION) / NULLIF(SUM("AI_Prompts_IntentIdentification"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY
      "Date"
  ), mpu AS (
    SELECT
      "Date",
      'MPU' AS "kpi_name",
      CAST(SUM("Missed_Utterance_MPU") AS DOUBLE PRECISION) / NULLIF(SUM("AI_Prompts_MPU"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY
      "Date"
  )
  SELECT
    *
  FROM auth
  UNION ALL
  SELECT
    *
  FROM intent_id
  UNION ALL
  SELECT
    *
  FROM mpu
  ORDER BY
    "Date",
    "kpi_name"
) AS virtual_table
GROUP BY
  kpi_name
ORDER BY
  "Rate" DESC
LIMIT 1000



SELECT
  kpi_name AS kpi_name,
  ROUND(SUM("total_aht") / SUM("conversation_count")) AS "AHT"
FROM (
  SELECT
    "Date",
    kpi_name,
    SUM(aht_sum) AS total_aht,
    SUM(conv_count) AS conversation_count,
    ROUND(SUM(aht_sum) / NULLIF(SUM(conv_count), 0), 2) AS kpi_value
  FROM (
    SELECT
      DATE("Date") AS "Date",
      'MPU AHT' AS kpi_name,
      SUM("MPU_AHT") AS aht_sum,
      COUNT("Conversation Id") AS conv_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Caller_Type" = 'Residential' AND NOT "MPU_AHT" IS NULL
    GROUP BY
      DATE("Date")
    UNION ALL
    SELECT
      DATE("Date") AS "Date",
      'Authentication AHT' AS kpi_name,
      SUM("Verification_AHT") AS aht_sum,
      COUNT("Conversation Id") AS conv_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Caller_Type" = 'Residential' AND NOT "Verification_AHT" IS NULL
    GROUP BY
      DATE("Date")
  ) AS sub
  GROUP BY
    "Date",
    kpi_name
  ORDER BY
    "Date",
    kpi_name
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
GROUP BY
  kpi_name
ORDER BY
  "AHT" DESC
LIMIT 1000


SELECT
  abandonment_type AS abandonment_type,
  ROUND(SUM("total_aht") / SUM("conversation_count")) AS "AHT"
FROM (
  SELECT
    "Date",
    abandonment_type,
    SUM(aht_sum) AS total_aht,
    SUM(conv_count) AS conversation_count,
    ROUND(CAST((
      SUM(aht_sum) / NULLIF(SUM(conv_count), 0)
    ) AS DECIMAL), 2) AS avg_aht
  FROM (
    SELECT
      DATE("Date") AS "Date",
      'AHT - Abandonment' AS abandonment_type,
      SUM("AHT") AS aht_sum,
      COUNT("Conversation Id") AS conv_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Abandonment by customer - flag" = 1
      AND "Caller_Type" = 'Residential'
      AND NOT "AHT" IS NULL
    GROUP BY
      DATE("Date")
    UNION ALL
    SELECT
      DATE("Date") AS "Date",
      'AHT - Other Calls' AS abandonment_type,
      SUM("AHT") AS aht_sum,
      COUNT("Conversation Id") AS conv_count
    FROM public."New_Republic_Dataset"
    WHERE
      "Abandonment by customer - flag" = 0
      AND "Caller_Type" = 'Residential'
      AND NOT "AHT" IS NULL
    GROUP BY
      DATE("Date")
  ) AS sub
  GROUP BY
    "Date",
    abandonment_type
  ORDER BY
    "Date",
    abandonment_type
) AS virtual_table
WHERE
  "Date" >= TO_DATE('2025-08-29', 'YYYY-MM-DD')
  AND "Date" < TO_DATE('2025-09-29', 'YYYY-MM-DD')
GROUP BY
  abandonment_type
ORDER BY
  "AHT" DESC
LIMIT 1000
