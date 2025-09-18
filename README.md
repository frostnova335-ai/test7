WITH case_manager_details AS (
  SELECT
    "Case_Manager",
    "Application_Date2",
    "Sales_Channel_Type",
    "Product",
    COUNT(*) AS No_of_Applications,
    SUM(CASE WHEN "NIGO_to_IGO_Conversion" = 1 THEN 1 ELSE 0 END) AS Num,
    AVG("TAT") AS Avg_TAT_In_Days,
    SUM("Revenue") AS Total_Revenue
  FROM "NIGO_APPLICATION_DATA"
  GROUP BY
    "Case_Manager",
    "Application_Date2",
    "Sales_Channel_Type",
    "Product"
),
case_manager_summary AS (
  SELECT
    "Case_Manager",
    SUM(No_of_Applications) AS No_of_Applications,
    SUM(Num) AS Num,
    AVG(Avg_TAT_In_Days) AS Avg_TAT_In_Days,
    SUM(Total_Revenue) AS Total_Revenue
  FROM case_manager_details
  GROUP BY "Case_Manager"
)
SELECT
  "Case_Manager",
  No_of_Applications,
  Num,
  ROUND(Num * 1.0 / NULLIF(No_of_Applications, 0), 2) AS NIGO_to_IGO_Conversion_Rate,
  Avg_TAT_In_Days,
  Total_Revenue
FROM case_manager_summary
ORDER BY "Case_Manager"
LIMIT 100;
