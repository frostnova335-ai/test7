SELECT
    CASE 
        WHEN "Escalated_2" = 'During Authentication' 
            THEN 'During Authentication'
        WHEN "Escalated_2" = 'After Authentication (MPU Only)' 
            THEN 'After Authentication'
        WHEN "Escalated_2" = 'After Authentication (MPU + Others)' 
            THEN 'After Authentication'
        WHEN "Escalated_2" = 'After Authentication (Others)' 
            THEN 'After Authentication'
    END AS "auth_stage"  -- Inner circle

   ,CASE
        WHEN "Escalated_2" = 'During Authentication' 
            THEN 'During Authentication'
        WHEN "Escalated_2" = 'After Authentication (MPU Only)' 
            THEN 'MPU Only'
        WHEN "Escalated_2" = 'After Authentication (MPU + Others)' 
            THEN 'MPU + Others'
        WHEN "Escalated_2" = 'After Authentication (Others)' 
            THEN 'Others'
    END AS "auth_detail"  -- Outer circle

   ,COUNT(*) AS "total_calls"

FROM "New_Republic_Dataset"
WHERE "Escalated" <> 'FALSE' 
  AND "Escalated_2" <> 'FALSE'
GROUP BY "auth_stage", "auth_detail";
