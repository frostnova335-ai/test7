✅ Chart 1: Archive/Unarchive Button Clicks
Type: Bar Chart
Insight: Volume of interactions per archive/unarchive action.

sql
Copy
Edit
SELECT 
  "custom_escalationType" AS "Button Click",
  COUNT(*) AS "Total Clicks"
FROM public."Mckesson_cmm_va"
WHERE "custom_escalationType" IS NOT NULL
GROUP BY "custom_escalationType"
ORDER BY "Total Clicks" DESC;
✅ Chart 2: Escalation Reason Breakdown
Type: Bar Chart
Insight: Top reasons for escalation.

sql
Copy
Edit
SELECT 
  "Escalation Reason",
  COUNT(*) AS "Total Escalations"
FROM public."Mckesson_cmm_va"
WHERE "Escalation Reason" IS NOT NULL
GROUP BY "Escalation Reason"
ORDER BY "Total Escalations" DESC;
✅ Chart 3: Convert to Classic Status Breakdown
Type: Horizontal Bar
Insight: Success/failure/agent-needed rates for Classic conversion.

sql
Copy
Edit
SELECT 
  "subUseCaseList" AS "Conversion Status",
  COUNT(*) * 100.0 / SUM(COUNT(*)) OVER() AS "Percentage"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'convert_to_classic'
GROUP BY "subUseCaseList"
ORDER BY "Percentage" DESC;
✅ Chart 4: Escalation After Classic Conversion
Type: Gauge
Insight: Classic conversions escalated to human agent.

sql
Copy
Edit
SELECT 
  COUNT(*) FILTER (WHERE "subflow" = 'convert_to_classic' AND "Escalated" = 'True') * 100.0 / 
  NULLIF(COUNT(*) FILTER (WHERE "subflow" = 'convert_to_classic'), 0) AS "Escalation Rate After Classic"
FROM public."Mckesson_cmm_va";
✅ Chart 5: Eligibility Call Distribution
Type: Bar Chart
Insight: Types of eligibility outcomes.

sql
Copy
Edit
SELECT 
  "subflow_list" AS "Eligibility Flow",
  COUNT(*) * 100.0 / SUM(COUNT(*)) OVER() AS "Percentage"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'eligibility'
GROUP BY "subflow_list"
ORDER BY "Percentage" DESC;
✅ Chart 6: User Problem Resolved
Type: Bar Chart
Insight: Which user fields resolved most queries.

sql
Copy
Edit
SELECT 
  "subflow_list" AS "Resolved By",
  COUNT(*) * 100.0 / SUM(COUNT(*)) OVER() AS "Resolution %"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'user_problem_resolved'
GROUP BY "subflow_list"
ORDER BY "Resolution %" DESC;
✅ Chart 7: Clicked Phone Number / Hard Copy
Type: Gauge
Insight: User interaction with links.

sql
Copy
Edit
SELECT 
  "subflow_list",
  COUNT(*) AS "Clicks"
FROM public."Mckesson_cmm_va"
WHERE "subflow_list" IN ('Click Phone Number', 'Click Hard Copy')
GROUP BY "subflow_list";
✅ Chart 8: Account Match Help Reason
Type: Bar Chart
Insight: Reasons why users needed help matching accounts.

sql
Copy
Edit
SELECT 
  "subflow_list" AS "Help Reason",
  COUNT(*) * 100.0 / SUM(COUNT(*)) OVER() AS "Percentage"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'account_match_help'
GROUP BY "subflow_list";
✅ Chart 9: Deflection Trend Over Time (Submit/Edit)
Type: Line Chart
Insight: % deflection (handled by bot) per day.

sql
Copy
Edit
SELECT 
  DATE("created.1") AS "Date",
  SUM("count_deflection") AS "Deflected",
  SUM("count_testrequest") AS "Total",
  ROUND(SUM("count_deflection") * 1.0 / NULLIF(SUM("count_testrequest"), 0), 4) AS "Deflection Rate"
FROM public."Mckesson_cmm_va"
GROUP BY DATE("created.1")
ORDER BY "Date";
✅ Chart 10: Deflection Trend for Archive/Unarchive
Type: Line Chart
Insight: % of archive/unarchive flows handled without escalation.

sql
Copy
Edit
SELECT 
  DATE("created.1") AS "Date",
  SUM("count_deflection_arch") AS "Deflected",
  SUM("count_arch_interactions") AS "Total",
  ROUND(SUM("count_deflection_arch") * 1.0 / NULLIF(SUM("count_arch_interactions"), 0), 4) AS "Deflection Rate"
FROM public."Mckesson_cmm_va"
GROUP BY DATE("created.1")
ORDER BY "Date";
✅ Chart 11: Subflow Escalation Reasons
Type: Bar Chart
Insight: Reasons for escalation in subflows (like upload, pick form, etc.)

sql
Copy
Edit
SELECT 
  "subflow_list" AS "Escalation Reason",
  COUNT(*) AS "Total Escalations"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'subflow_escalation'
GROUP BY "subflow_list"
ORDER BY "Total Escalations" DESC;
✅ Chart 12: Button Clicks (Upload, Update, Drug Change)
Type: Bar Chart
Insight: Usage of form buttons by users.

sql
Copy
Edit
SELECT 
  "custom_escalationType" AS "Button Click",
  COUNT(*) AS "Total"
FROM public."Mckesson_cmm_va"
WHERE "custom_escalationType" IN (
  'Upload Documents', 'Upload Doc to Request', 'Update Answers', 
  'Upload Doc Something Else', 'Change Drug Quantity', 'Change Drug Strength', 
  'Fax Doc', 'Fax Doc Status'
)
GROUP BY "custom_escalationType"
ORDER BY "Total" DESC;
✅ Chart 13: Last Intent Triggered Before Escalation
Type: Bar Chart
Insight: Which intents most frequently lead to escalation.

sql
Copy
Edit
SELECT 
  "triggeredIntent" AS "Intent",
  COUNT(*) AS "Escalations"
FROM public."Mckesson_cmm_va"
WHERE "Escalated" = 'True'
GROUP BY "triggeredIntent"
ORDER BY "Escalations" DESC;
✅ Chart 14: Primary Intent Distribution
Type: Bar Chart
Insight: Overall conversation intent distribution.

sql
Copy
Edit
SELECT 
  "triggeredIntent" AS "Intent",
  COUNT(*) AS "Total Conversations"
FROM public."Mckesson_cmm_va"
GROUP BY "triggeredIntent"
ORDER BY "Total Conversations" DESC;
✅ Chart 15: Key Retrieval Flow
Type: Bar Chart
Insight: User interaction with key retrieval and entry.

sql
Copy
Edit
SELECT 
  "request status" AS "Key Status",
  COUNT(*) AS "Total"
FROM public."Mckesson_cmm_va"
WHERE "request status" IS NOT NULL
GROUP BY "request status"
ORDER BY "Total" DESC;
