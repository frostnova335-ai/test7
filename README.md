WITH misclassification AS (
    SELECT
        'AI Misclassification Rate' AS "kpi_name",
        COUNT(CASE 
                WHEN "Intent" = 'MPU' 
                     AND "Resolution Codes" <> 'MPU'
                THEN "Conversation Id" END) * 1.0
        / NULLIF(COUNT(CASE WHEN "Intent" = 'MPU' THEN "Conversation Id" END), 0) 
        AS "kpi_value"
    FROM public."New_Republic_Dataset"
),

missed_utterance AS (
    SELECT
        'Missed Utterance Rate' AS "kpi_name",
        SUM("Missed_Utterance") * 1.0
        / NULLIF(SUM("Number of Prompts from AI"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
),

prompt_success AS (
    SELECT
        'Prompt Success Rate' AS "kpi_name",
        SUM("Number of Successful Prompts from AI") * 1.0
        / NULLIF(SUM("Number of Prompts from AI"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
)

SELECT * FROM misclassification
UNION ALL
SELECT * FROM missed_utterance
UNION ALL
SELECT * FROM prompt_success;
