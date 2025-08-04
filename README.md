SELECT
  "custom_escalated_reason" AS reason,
  ROUND(COUNT(*) * 100.0 / SUM(COUNT(*)) OVER (), 1) AS percent
FROM public."Mckesson_cmm_va"
WHERE "custom_escalationType" = 'Eligibility'
GROUP BY reason
ORDER BY percent DESC;
