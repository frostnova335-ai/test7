
# Superset Dashboard SQL Queries and Descriptions

This document contains SQL queries and plain-language explanations for each chart and panel in your Amelia Performance Dashboard.  
Replace `{{ start_date }}` and `{{ end_date }}` with your desired date range or Superset date filters.

---

## 1. Total Interactions
```sql
SELECT 
  COUNT(DISTINCT "Conversation Id") AS "total_interactions"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }};
```
**Description:** Counts unique conversations sent to Amelia in the selected time window — the overall volume of user interactions.

---

## 2. Request Keys
```sql
SELECT 
  SUM(COALESCE("count_requestid", 0)) AS "total_request_keys"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }};
```
**Description:** Totals all request keys submitted by users in the period, indicating how many backend/lookups were attempted or triggered.

---

## 3. Billed Interactions
```sql
SELECT 
  COUNT(DISTINCT "Conversation Id") AS "billed_interactions"
FROM public."Mckesson.cmm.va"
WHERE 
  (
    (
      "Amelia Abandoned" = 'True' 
      AND "Amelia Category" = 'PA Status'
    )
    OR ("count_deflection_edit" = 1)
    OR ("count_deflection_archive_unarchive" = 1)
  )
  AND TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }};
```
**Description:** Counts conversations considered billable: PA Status abandoned (timeout/user left) or deflected via edit/submit or archive/unarchive logic.

---

## 4. Hourly Interactions with Outcome Breakdown (Last 7 Days)
```sql
SELECT 
  DATE_TRUNC('hour', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "hour_bucket",
  COUNT(*) AS "total_interactions",
  SUM(CASE WHEN "Amelia Handled" = 'True' THEN 1 ELSE 0 END) AS "amelia_handled",
  SUM(CASE WHEN "Escalated" = 'True' THEN 1 ELSE 0 END) AS "transferred",
  SUM(CASE WHEN "Amelia Abandoned" = 'True' THEN 1 ELSE 0 END) AS "abandoned"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') >= NOW() - INTERVAL '7 days'
GROUP BY 1
ORDER BY 1;
```
**Description:** Shows interaction volume by hour over the last 7 days, broken into handled, transferred, and abandoned, enabling trend analysis and capacity/load visibility.

---

## 5. Interaction Outcome Distribution
```sql
SELECT 
  CASE 
    WHEN "Amelia Handled" = 'True' THEN 'Amelia Handled'
    WHEN "Escalated" = 'True' THEN 'Transferred'
    WHEN "Amelia Abandoned" = 'True' THEN 'Abandoned'
    ELSE 'Other'
  END AS "outcome",
  COUNT(DISTINCT "Conversation Id") AS "count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY "count" DESC;
```
**Description:** Categorizes each conversation into outcome buckets—successfully handled, escalated, or abandoned—to show effectiveness and failure points.

---

## 6. Top 10 Transferred Reasons
```sql
SELECT 
  "Escalation Reason" AS "transfer_reason",
  COUNT(DISTINCT "Conversation Id") AS "reason_count"
FROM public."Mckesson.cmm.va"
WHERE "Escalated" = 'True'
  AND TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY "reason_count" DESC
LIMIT 10;
```
**Description:** Ranks the top reasons Amelia escalated conversations to human coordinators—helps identify friction or missing automation.

---

## 7. Last Intent Triggered Before Escalation
```sql
SELECT 
  "subflow" AS "last_intent_before_escalation",
  COUNT(DISTINCT "Conversation Id") AS "count"
FROM public."Mckesson.cmm.va"
WHERE "Escalated" = 'True'
  AND TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY "count" DESC
LIMIT 20;
```
**Description:** Surfaces the most recent intent or subflow the user was in when an escalation occurred—useful for pinpointing escalation triggers.

---

## 8. Primary Intent Distribution
```sql
SELECT 
  "Amelia Category" AS "primary_intent",
  COUNT(DISTINCT "Conversation Id") AS "count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY "count" DESC;
```
**Description:** Shows which major categories of intents Amelia handled (e.g., PA Status, Edit/Submit, Archive/Unarchive), giving a sense of usage mix.

---

## 9. Deflection Ratio Per Day
```sql
SELECT 
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  SUM(
    CASE 
      WHEN "count_deflection_pa_status" = 1 THEN 1
      WHEN "count_deflection_edit" = 1 THEN 1
      WHEN "count_deflection_archive_unarchive" = 1 THEN 1
      ELSE 0
    END
  )::float / COUNT(DISTINCT "Conversation Id") AS "deflection_ratio"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY 1;
```
**Description:** Daily percentage of conversations that were successfully deflected (across PA Status, Edit/Submit, Archive/Unarchive) versus total volume.

---

## 10. Deflection Trend by Flow
```sql
SELECT 
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'PA Status' AS "flow",
  SUM(CASE WHEN "count_deflection_pa_status" = 1 THEN 1 ELSE 0 END) AS "deflected_count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

UNION ALL

SELECT 
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'Edit/Submit' AS "flow",
  SUM(CASE WHEN "count_deflection_edit" = 1 THEN 1 ELSE 0 END) AS "deflected_count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

UNION ALL

SELECT 
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  'Archive/Unarchive' AS "flow",
  SUM(CASE WHEN "count_deflection_archive_unarchive" = 1 THEN 1 ELSE 0 END) AS "deflected_count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1

ORDER BY "day", "flow";
```
**Description:** Tracks deflection volume over time, split by major flow categories, to compare effectiveness trends across pathways.

---

## 11. Sentiment Distribution
```sql
SELECT 
  "sentiment",
  COUNT(DISTINCT "Conversation Id") AS "count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
ORDER BY "count" DESC;
```
**Description:** Breaks down conversations by sentiment label (Positive / Neutral / Negative), reflecting user emotion distribution.

---

## 12. Sentiment Trend Over Time
```sql
SELECT 
  DATE_TRUNC('day', TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS')) AS "day",
  "sentiment",
  COUNT(DISTINCT "Conversation Id") AS "count"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1, 2
ORDER BY "day";
```
**Description:** Shows how sentiment shifts day-to-day, enabling detection of improving or degrading user satisfaction over time.

---

## 13. Sentiment Score vs. Average Handle Time (Scatter)
```sql
SELECT 
  "sentimentScore" AS "sentiment_score",
  "aht_sec" AS "handle_time_seconds"
FROM public."Mckesson.cmm.va"
WHERE "sentimentScore" IS NOT NULL 
  AND "aht_sec" IS NOT NULL
  AND TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }};
```
**Description:** Scatter plot data showing relationship between sentiment intensity and how long interactions took — can reveal if longer sessions correlate with frustration (negative sentiment) or satisfaction.

---

## 14. Top 10 Repeat Users
```sql
SELECT 
  "User Email" AS "user_id",
  COUNT(DISTINCT "Conversation Id") AS "sessions_per_user"
FROM public."Mckesson.cmm.va"
WHERE TO_TIMESTAMP("Created", 'MM/DD/YYYY HH24:MI:SS') BETWEEN {{ start_date }} AND {{ end_date }}
GROUP BY 1
HAVING COUNT(DISTINCT "Conversation Id") > 1
ORDER BY "sessions_per_user" DESC
LIMIT 10;
```
**Description:** Identifies users who interacted multiple times in the period—signals repeat engagement or unresolved issues.
