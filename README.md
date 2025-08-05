✅ Chart 1: Archive/Unarchive Button Clicks
SQL:

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
Why these columns:

"custom_escalationType" tracks specific user actions like Archive/Unarchive, Upload, Fax.

This column represents explicit button clicks, making it ideal for interaction analysis.

Business Meaning:
Shows which self-service actions are used most often. Helps assess adoption of automation features like archive requests or document uploads.

✅ Chart 2: Escalation Reason Breakdown
SQL:

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
Why these columns:

"Escalation Reason" directly identifies why conversations failed and needed human intervention.

Business Meaning:
Highlights top failure reasons where the virtual assistant couldn't resolve the issue. Vital for reducing escalations through better automation design.

✅ Chart 3: Convert to Classic Status Breakdown
SQL:

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
Why these columns:

"subflow" filters only the Classic Conversion flow.

"subUseCaseList" describes if the conversion succeeded or failed.

Business Meaning:
Shows how effective the "Convert to Classic" process is. High success rates indicate good automation quality in that subflow.

✅ Chart 4: Escalation After Classic Conversion
SQL:

sql
Copy
Edit
SELECT 
  COUNT(*) FILTER (
    WHERE "subflow" = 'convert_to_classic' AND "Escalated" = 'True'
  ) * 100.0 / NULLIF(COUNT(*) FILTER (
    WHERE "subflow" = 'convert_to_classic'), 0) AS "Escalation Rate After Classic"
FROM public."Mckesson_cmm_va";
Why these columns:

Filters classic conversion interactions and checks if they escalated.

Business Meaning:
Shows how often users needed agent help even after using the conversion flow. Reveals automation gap.

✅ Chart 5: Eligibility Call Distribution
SQL:

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
Why these columns:

"subflow" filters eligibility flow.

"subflow_list" represents specific outcome steps within it.

Business Meaning:
Shows how users navigate eligibility tasks. Useful for optimizing UI or reducing confusion.

✅ Chart 6: User Problem Resolved
SQL:

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
Why these columns:

Focuses on how issues were resolved (e.g. by drug, DOB, etc.)

Business Meaning:
Highlights the most effective info fields in resolving requests. Useful for intent tuning.

✅ Chart 7: Clicked Phone Number / Hard Copy
SQL:

sql
Copy
Edit
SELECT 
  "subflow_list",
  COUNT(*) AS "Clicks"
FROM public."Mckesson_cmm_va"
WHERE "subflow_list" IN ('Click Phone Number', 'Click Hard Copy')
GROUP BY "subflow_list";
Why these columns:

"subflow_list" captures low-effort interactions like clicking links.

Business Meaning:
Indicates how often users attempt to bypass automation (e.g., call directly). Signals where friction exists.

✅ Chart 8: Account Match Help Reasons
SQL:

sql
Copy
Edit
SELECT 
  "subflow_list" AS "Help Reason",
  COUNT(*) * 100.0 / SUM(COUNT(*)) OVER() AS "Percentage"
FROM public."Mckesson_cmm_va"
WHERE "subflow" = 'account_match_help'
GROUP BY "subflow_list";
Why these columns:

Filters to account match flow and splits by reason users needed help.

Business Meaning:
Reveals friction points in account matching like DOB mismatch, which could be auto-resolved.

✅ Chart 9: Deflection Trend Over Time (Submit/Edit)
SQL:

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
Why these columns:

Calculates daily deflection rate: "count_deflection" / "count_testrequest"

Business Meaning:
Trend of how many requests Amelia handled without human help. Higher = better automation.

✅ Chart 10: Archive/Unarchive Deflection Trend
SQL:

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
Why these columns:

Same deflection logic but scoped to archive use-case.

Business Meaning:
Measures effectiveness of archive/unarchive automation over time.

✅ Chart 11: Subflow Escalation Reasons
SQL:

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
Why these columns:

"subflow" filters subflow failures, and "subflow_list" identifies root reason.

Business Meaning:
Shows which specific actions most often lead to failure/escalation in subflows.

✅ Chart 12: Upload/Update/Drug Change Button Clicks
SQL:

sql
Copy
Edit
SELECT 
  "custom_escalationType",
  COUNT(*) AS "Total"
FROM public."Mckesson_cmm_va"
WHERE "custom_escalationType" IN (
  'Upload Documents', 'Upload Doc to Request', 'Update Answers', 
  'Upload Doc Something Else', 'Change Drug Quantity', 'Change Drug Strength', 
  'Fax Doc', 'Fax Doc Status'
)
GROUP BY "custom_escalationType"
ORDER BY "Total" DESC;
Why these columns:

Filters button clicks across high-traffic interactions.

Business Meaning:
Ranks which document or drug-related buttons are used most. Highlights user priorities.

✅ Chart 13: Intent Before Escalation
SQL:

sql
Copy
Edit
SELECT 
  "triggeredIntent",
  COUNT(*) AS "Escalations"
FROM public."Mckesson_cmm_va"
WHERE "Escalated" = 'True'
GROUP BY "triggeredIntent"
ORDER BY "Escalations" DESC;
Why these columns:

Shows which top-level intents are most likely to escalate.

Business Meaning:
Pinpoints automation failure in specific use-cases. Useful for retraining or rule changes.

✅ Chart 14: Primary Intent Distribution
SQL:

sql
Copy
Edit
SELECT 
  "triggeredIntent",
  COUNT(*) AS "Total Conversations"
FROM public."Mckesson_cmm_va"
GROUP BY "triggeredIntent"
ORDER BY "Total Conversations" DESC;
Why these columns:

Tallies all conversations by intent type.

Business Meaning:
Shows which intents are most in-demand, which may require deeper optimization.

✅ Chart 15: Key Retrieval Outcomes
SQL:

sql
Copy
Edit
SELECT 
  "request status",
  COUNT(*) AS "Total"
FROM public."Mckesson_cmm_va"
WHERE "request status" IS NOT NULL
GROUP BY "request status"
ORDER BY "Total" DESC;
Why these columns:

"request status" shows whether key was entered, matched, or skipped.

Business Meaning:
Highlights how successful key retrieval flows are.
