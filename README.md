WITH base AS (
  SELECT
    "Date",
    SUM("Missed_Utterance")::float AS missed,
    SUM("Number of Prompts from AI")::float AS total_prompts
  FROM public."New_Republic_Dataset"
  GROUP BY "Date"
)
SELECT "Date", 'Missed Utterance' AS "category",
       (missed / NULLIF(total_prompts,0)) * 100 AS "value"
FROM base
UNION ALL
SELECT "Date", 'Successful Utterance' AS "category",
       ((total_prompts - missed) / NULLIF(total_prompts,0)) * 100 AS "value"
FROM base
ORDER BY "Date", "category";
