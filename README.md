WITH base AS (
    SELECT
        CASE
            WHEN "Out of Scope Live Agent Handoff During Authentication" IS NOT NULL 
                 AND "Out of Scope Live Agent Handoff During Authentication" <> 'FALSE'
            THEN 'During Authentication'
            
            WHEN ("Out of Scope Live Agent Handoff After Authentication (MPU Only)" IS NOT NULL 
                  AND "Out of Scope Live Agent Handoff After Authentication (MPU Only)" <> 'FALSE')
              OR ("Out of Scope Live Agent Handoff After Authentication (MPU + Others)" IS NOT NULL 
                  AND "Out of Scope Live Agent Handoff After Authentication (MPU + Others)" <> 'FALSE')
              OR ("Out of Scope Live Agent Handoff After Authentication (Others)" IS NOT NULL 
                  AND "Out of Scope Live Agent Handoff After Authentication (Others)" <> 'FALSE')
            THEN 'After Authentication'
        END AS inner_category,

        CASE
            WHEN "Out of Scope Live Agent Handoff During Authentication" IS NOT NULL 
                 AND "Out of Scope Live Agent Handoff During Authentication" <> 'FALSE'
            THEN 'Escalated during authentication'

            WHEN "Out of Scope Live Agent Handoff After Authentication (MPU Only)" IS NOT NULL 
                 AND "Out of Scope Live Agent Handoff After Authentication (MPU Only)" <> 'FALSE'
            THEN 'Escalated after authentication (MPU only)'

            WHEN "Out of Scope Live Agent Handoff After Authentication (MPU + Others)" IS NOT NULL 
                 AND "Out of Scope Live Agent Handoff After Authentication (MPU + Others)" <> 'FALSE'
            THEN 'Escalated after authentication (MPU + Others)'

            WHEN "Out of Scope Live Agent Handoff After Authentication (Others)" IS NOT NULL 
                 AND "Out of Scope Live Agent Handoff After Authentication (Others)" <> 'FALSE'
            THEN 'Escalated after authentication (Others)'
        END AS outer_category
    FROM "New_Republic_Dataset"
),
total AS (
    SELECT COUNT(*)::numeric AS total_count FROM base WHERE inner_category IS NOT NULL
)
SELECT 
    inner_category AS ring,
    outer_category AS category,
    ROUND((COUNT(*) * 100.0 / (SELECT total_count FROM total))::numeric, 2) AS percentage
FROM base
WHERE inner_category IS NOT NULL
GROUP BY inner_category, outer_category;
