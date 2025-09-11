🔹 Core SQL Queries (with inverted commas)
1. Broker-wise Status Breakdown (IGO vs NIGO)
SELECT 
    "Supplier_Name",
    "Status",
    COUNT(*) AS "Policy_Count"
FROM "policies"
GROUP BY "Supplier_Name", "Status"
ORDER BY "Supplier_Name", "Policy_Count" DESC;


📊 Use: Stacked Bar Chart → Helps identify which broker has higher NIGO volume.

2. Product NIGO Percentage
SELECT 
    "Product",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS "NIGO_Percentage",
    COUNT(*) AS "Total_Policies"
FROM "policies"
GROUP BY "Product"
ORDER BY "NIGO_Percentage" DESC;


📊 Use: Bar Chart (sorted by NIGO%) → Shows which products are causing most rejections.

3. Policy Status Trend Over Time
SELECT 
    DATE_TRUNC('month', "Application_Date") AS "Month",
    "Status",
    COUNT(*) AS "Policy_Count"
FROM "policies"
GROUP BY DATE_TRUNC('month', "Application_Date"), "Status"
ORDER BY "Month" ASC;


📊 Use: Line Chart → Tracks NIGO/IGO patterns monthly.

4. Sales Channel NIGO %
SELECT 
    "Sales_Channel_Type",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS "NIGO_Percentage",
    COUNT(*) AS "Total_Policies"
FROM "policies"
GROUP BY "Sales_Channel_Type";


📊 Use: Pie/Bar Chart → Compare Bank vs Broker performance.

5. Top 5 Worst Performing Brokers (NIGO Count)
SELECT 
    "Supplier_Name",
    COUNT(*) AS "NIGO_Count"
FROM "policies"
WHERE "Status" = 'NIGO'
GROUP BY "Supplier_Name"
ORDER BY "NIGO_Count" DESC
LIMIT 5;


📊 Use: Bar Chart → Highlights which brokers need training/process improvement.

🔹 Advanced / Derivative Queries
6. NIGO to IGO Ratio (Broker Performance Score)
SELECT 
    "Supplier_Name",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) AS "NIGO_Count",
    SUM(CASE WHEN "Status" = 'IGO' THEN 1 ELSE 0 END) AS "IGO_Count",
    ROUND(
        SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END)::decimal /
        NULLIF(SUM(CASE WHEN "Status" = 'IGO' THEN 1 ELSE 0 END), 0), 2
    ) AS "NIGO_to_IGO_Ratio"
FROM "policies"
GROUP BY "Supplier_Name"
ORDER BY "NIGO_to_IGO_Ratio" DESC;


📊 Use: Heatmap/Table with color formatting → Higher ratio = poor performing broker.

7. Month-over-Month NIGO % Change
SELECT
    DATE_TRUNC('month', "Application_Date") AS "Month",
    ROUND(
        SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 
        2
    ) AS "NIGO_Percentage"
FROM "policies"
GROUP BY DATE_TRUNC('month', "Application_Date")
ORDER BY "Month" ASC;


📊 Use: Line Chart → Shows improvement or deterioration trend in data quality.

8. Broker & Product Combination (Problem Areas)
SELECT 
    "Supplier_Name",
    "Product",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) AS "NIGO_Count",
    COUNT(*) AS "Total_Policies",
    ROUND(
        SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 
        2
    ) AS "NIGO_Percentage"
FROM "policies"
GROUP BY "Supplier_Name", "Product"
HAVING SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) > 0
ORDER BY "NIGO_Percentage" DESC;


📊 Use: TreeMap or Pivot Table → Helps find which product under which broker is failing most.

9. Channel + Product NIGO Hotspots
SELECT 
    "Sales_Channel_Type",
    "Product",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) AS "NIGO_Count",
    ROUND(
        SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 
        2
    ) AS "NIGO_Percentage"
FROM "policies"
GROUP BY "Sales_Channel_Type", "Product"
ORDER BY "NIGO_Percentage" DESC;


📊 Use: Clustered Bar Chart → Compares NIGO issues across channels & products.

10. Broker Ranking Dashboard Metric
SELECT 
    "Supplier_Name",
    COUNT(*) AS "Total_Policies",
    SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) AS "NIGO_Count",
    ROUND(
        SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 
        2
    ) AS "NIGO_Percentage",
    RANK() OVER (ORDER BY SUM(CASE WHEN "Status" = 'NIGO' THEN 1 ELSE 0 END) DESC) AS "Broker_Rank"
FROM "policies"
GROUP BY "Supplier_Name"
ORDER BY "Broker_Rank";


📊 Use: Ranking Table → Helps management identify "Top bad brokers".
