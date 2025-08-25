SELECT
  'MPU AHT' AS "kpi_name",
  AVG("MPU_AHT") AS "kpi_value"
FROM public."New_Republic_Dataset"
WHERE "Amelia Handled" = 1

UNION ALL

SELECT
  'Verification AHT' AS "kpi_name",
  AVG("Verification_AHT") AS "kpi_value"
FROM public."New_Republic_Dataset"
WHERE "Amelia Handled" = 1;
