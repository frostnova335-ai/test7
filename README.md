WITH auth AS (
  SELECT
    'Auth Missed Utterance Rate' AS "kpi_name",
    SUM("Missed_Utterance_Auth")::float
    / NULLIF(SUM("AI_Prompts_Auth"), 0) AS "kpi_value"
  FROM public."New_Republic_Dataset"
),
intent_id AS (
  SELECT
    'Intent Identification Missed Utterance Rate' AS "kpi_name",
    SUM("Missed_Utterance_IntentIdentification")::float
    / NULLIF(SUM("AI_Prompts_IntentIdentification"), 0) AS "kpi_value"
  FROM public."New_Republic_Dataset"
),
mpu AS (
  SELECT
    'MPU Missed Utterance Rate' AS "kpi_name",
    SUM("Missed_Utterance_MPU")::float
    / NULLIF(SUM("AI_Prompts_MPU"), 0) AS "kpi_value"
  FROM public."New_Republic_Dataset"
)
SELECT * FROM auth
UNION ALL
SELECT * FROM intent_id
UNION ALL
SELECT * FROM mpu;
