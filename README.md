
SELECT 
  "Created"::date AS date,
  SUM(CASE WHEN "count_deflection" > 0 THEN "count_deflection" ELSE 0 END) AS deflected,
  SUM(CASE WHEN "count_deflection_pa_status" > 0 THEN "count_deflection_pa_status" ELSE 0 END) AS deflected_pa_status,
  SUM(CASE WHEN "count_deflection_edit" > 0 THEN "count_deflection_edit" ELSE 0 END) AS deflected_with_subflow,
  SUM(CASE WHEN "count_abandoned" > 0 THEN "count_abandoned" ELSE 0 END) AS generated_abandon
FROM public."Mckesson_cmm_va"
GROUP BY date
ORDER BY date
