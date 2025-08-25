WITH misclassification AS (
  SELECT
    'AI Misclassification Rate' AS "kpi_name",
    (
      COUNT(*) FILTER (
        WHERE "Intent" = 'MPU'
          AND "Resolution Codes" IS DISTINCT FROM 'MPU'
      )
    )::float
    / NULLIF(
        COUNT(*) FILTER (WHERE "Intent" = 'MPU'),
        0
      ) AS "kpi_value"
  FROM public."New_Republic_Dataset"
),
missed_utterance AS (
  SELECT
    'Missed Utterance Rate' AS "kpi_name",
    SUM("Missed_Utterance")::float
    / NULLIF(SUM("Number of Prompts from AI"), 0) AS "kpi_value"
  FROM public."New_Republic_Dataset"
),
prompt_success AS (
  SELECT
    'Prompt Success Rate' AS "kpi_name",
    SUM("Number of Successful Prompts from AI")::float
    / NULLIF(SUM("Number of Prompts from AI"), 0) AS "kpi_value"
  FROM public."New_Republic_Dataset"
)
SELECT * FROM misclassification
UNION ALL
SELECT * FROM missed_utterance
UNION ALL
SELECT * FROM prompt_success;
