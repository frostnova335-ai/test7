WITH misclassification AS (
    SELECT
        'AI Misclassification Rate' AS "kpi_name",
        "module",
        COUNT(
            CASE 
                WHEN "is_residential" = 1
                  AND "is_authenticated" = 1
                  AND "actual_intent" != 'MPU'
                  AND "identified_intent" = 'MPU'
                THEN "call_id" END
        ) * 1.0
        / NULLIF(
            COUNT(
                CASE 
                    WHEN "is_residential" = 1
                      AND "is_authenticated" = 1
                      AND "identified_intent" = 'MPU'
                    THEN "call_id" END
            ), 0
        ) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY "module"
),

missed_utterance AS (
    SELECT
        'Missed Utterance Rate' AS "kpi_name",
        "module",
        COUNT(
            CASE 
                WHEN "prompt_result" IN ('invalid_response','no_response','abandonment','transfer')
                THEN "prompt_id" END
        ) * 1.0
        / NULLIF(COUNT("prompt_id"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY "module"
),

prompt_success AS (
    SELECT
        'Prompt Success Rate' AS "kpi_name",
        "module",
        COUNT(
            CASE 
                WHEN "prompt_result" = 'expected_response'
                THEN "prompt_id" END
        ) * 1.0
        / NULLIF(COUNT("prompt_id"), 0) AS "kpi_value"
    FROM public."New_Republic_Dataset"
    GROUP BY "module"
)

SELECT * FROM misclassification
UNION ALL
SELECT * FROM missed_utterance
UNION ALL
SELECT * FROM prompt_success;
