CASE 
    WHEN "Escalated_2" = 'During Authentication' THEN 'During Authentication'
    WHEN "Escalated_2" LIKE 'After Authentication (MPU Only)' THEN 'After Authentication - MPU Only'
    WHEN "Escalated_2" LIKE 'After Authentication (MPU + Others)' THEN 'After Authentication - MPU + Others'
    WHEN "Escalated_2" LIKE 'After Authentication (Others)' THEN 'After Authentication - Others'
END AS auth_stage,

CASE
    WHEN "Escalated_2" = 'During Authentication' THEN 'During Authentication'
    WHEN "Escalated_2" LIKE '%MPU Only%' THEN 'MPU Only'
    WHEN "Escalated_2" LIKE '%MPU + Others%' THEN 'MPU + Others'
    WHEN "Escalated_2" LIKE '%Others%' THEN 'Others'
END AS auth_detail
