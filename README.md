interaction analysis -

SELECT 
  created::date AS date, 
  COUNT("ConversationId") AS interactions_count
FROM public."Mckesson_cmm_va"
GROUP BY date
ORDER BY date


deflection trend -

SELECT 
  created::date AS date,
  SUM(CASE WHEN deflectionstatus = 'Deflected' THEN 1 ELSE 0 END) AS deflected,
  SUM(CASE WHEN deflectionstatus = 'Deflected PA Status' THEN 1 ELSE 0 END) AS deflected_pa_status,
  SUM(CASE WHEN deflectionstatus = 'Deflected with Subflow' THEN 1 ELSE 0 END) AS deflected_with_subflow,
  SUM(CASE WHEN deflectionstatus = 'Generated Abandon' THEN 1 ELSE 0 END) AS generated_abandon
FROM public."Mckesson_cmm_va"
GROUP BY date
ORDER BY date



billed interaction -
SELECT 
  created::date AS date,
  SUM(billed_interactions) AS billed_interactions,
  SUM(deflected_pa_status) AS deflected_pa_status,
  SUM(over_deflection_limit) AS over_deflection_limit,
  SUM(over_deflection_allowance) AS over_deflection_allowance
FROM public."Mckesson_cmm_va"
GROUP BY date
ORDER BY date



eligibility call







