Suggested SQL Queries for Superset
1. Broker Performance (IGO vs NIGO count by Supplier_Name)
SELECT 
    Supplier_Name,
    Status,
    COUNT(*) AS policy_count
FROM policies
GROUP BY Supplier_Name, Status
ORDER BY Supplier_Name, policy_count DESC;


📊 Chart: Stacked Bar (Supplier_Name on X-axis, policy count split by Status)

2. Product Analysis (NIGO percentage by Product)
SELECT 
    Product,
    SUM(CASE WHEN Status = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS nigo_percentage,
    COUNT(*) AS total_policies
FROM policies
GROUP BY Product
ORDER BY nigo_percentage DESC;


📊 Chart: Horizontal Bar (Products sorted by NIGO %)

3. Policy Status Trend (IGO vs NIGO over time)
SELECT 
    DATE_TRUNC('month', Application_Date) AS month,
    Status,
    COUNT(*) AS policy_count
FROM policies
GROUP BY DATE_TRUNC('month', Application_Date), Status
ORDER BY month ASC;


📊 Chart: Line Chart (Month vs Policy Count, split by Status)

4. Sales Channel Contribution (Bank vs Broker – NIGO %)
SELECT 
    Sales_Channel_Type,
    SUM(CASE WHEN Status = 'NIGO' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS nigo_percentage,
    COUNT(*) AS total_policies
FROM policies
GROUP BY Sales_Channel_Type;


📊 Chart: Pie Chart or Bar Chart

5. Worst Performing Brokers (Top 5 by NIGO count)
SELECT 
    Supplier_Name,
    COUNT(*) AS nigo_count
FROM policies
WHERE Status = 'NIGO'
GROUP BY Supplier_Name
ORDER BY nigo_count DESC
LIMIT 5;


📊 Chart: Bar Chart (Top 5 problematic brokers)

6. Derivative Metric: NIGO to IGO Ratio
SELECT 
    Supplier_Name,
    SUM(CASE WHEN Status = 'NIGO' THEN 1 ELSE 0 END) AS nigo_count,
    SUM(CASE WHEN Status = 'IGO' THEN 1 ELSE 0 END) AS igo_count,
    (SUM(CASE WHEN Status = 'NIGO' THEN 1 ELSE 0 END) * 1.0 /
     NULLIF(SUM(CASE WHEN Status = 'IGO' THEN 1 ELSE 0 END), 0)) AS nigo_to_igo_ratio
FROM policies
GROUP BY Supplier_Name
ORDER BY nigo_to_igo_ratio DESC;


📊 Chart: Table with Conditional Formatting (higher ratio = more issues)
