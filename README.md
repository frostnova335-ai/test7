SELECT
  "transcriptId" AS "Call ID",

  "Intent" AS "Intent",

  /* ===================== NPS ===================== */
  CASE
    WHEN CAST(NULLIF(regexp_replace("NPS"::text, '[^0-9]', '', 'g'), '') AS INTEGER) >= 9 THEN
      '<span style="background:#dcfce7;color:#166534;padding:4px 8px;border-radius:6px;font-weight:600;">😍 '
      || "NPS" || '</span>'

    WHEN CAST(NULLIF(regexp_replace("NPS"::text, '[^0-9]', '', 'g'), '') AS INTEGER) >= 7 THEN
      '<span style="background:#fef3c7;color:#92400e;padding:4px 8px;border-radius:6px;font-weight:600;">🙂 '
      || "NPS" || '</span>'

    ELSE
      '<span style="background:#fee2e2;color:#991b1b;padding:4px 8px;border-radius:6px;font-weight:600;">😠 '
      || "NPS" || '</span>'
  END AS "NPS",

  /* ===================== Churn Propensity (CATEGORICAL) ===================== */
  CASE
    WHEN "Churn_Propensity" ILIKE '%High%' THEN
      '<span style="background:#fee2e2;color:#991b1b;padding:4px 8px;border-radius:6px;font-weight:600;">⚠️ High</span>'

    WHEN "Churn_Propensity" ILIKE '%Medium%' THEN
      '<span style="background:#fef3c7;color:#92400e;padding:4px 8px;border-radius:6px;font-weight:600;">🟠 Medium</span>'

    WHEN "Churn_Propensity" ILIKE '%Low%' THEN
      '<span style="background:#dcfce7;color:#166534;padding:4px 8px;border-radius:6px;font-weight:600;">🟢 Low</span>'

    ELSE
      '<span style="background:#e5e7eb;color:#374151;padding:4px 8px;border-radius:6px;font-weight:600;">'
      || "Churn_Propensity" || '</span>'
  END AS "Churn Propensity",

  /* ===================== Churn Signals ===================== */
  '<span style="color:#1f2937;font-weight:600;">🚨 '
  || "Churn_Signals" || '</span>'
  AS "Churn Signals",

  /* ===================== Emotion ===================== */
  CASE "Emotion"
    WHEN 'Angry' THEN '<span style="color:#b91c1c;font-weight:600;">😡 Angry</span>'
    WHEN 'Frustrated' THEN '<span style="color:#c2410c;font-weight:600;">😠 Frustrated</span>'
    WHEN 'Neutral' THEN '<span style="color:#374151;font-weight:600;">😐 Neutral</span>'
    WHEN 'Happy' THEN '<span style="color:#15803d;font-weight:600;">😊 Happy</span>'
    ELSE '<span style="color:#1f2937;">🙂 ' || "Emotion" || '</span>'
  END AS "Emotion",

  /* ===================== Churn Reasoning ===================== */
  '<div style="background:#f9fafb;padding:8px;border-left:4px solid #6366f1;border-radius:6px;line-height:1.4;">🧠 '
  || "Churn_Reasoning" || '</div>'
  AS "Churn Reasoning"

FROM public."hnb_data"

WHERE
  "Churn_Signals" NOT IN ('-')

ORDER BY
  CASE
    WHEN "Churn_Propensity" ILIKE '%High%' THEN 1
    WHEN "Churn_Propensity" ILIKE '%Medium%' THEN 2
    WHEN "Churn_Propensity" ILIKE '%Low%' THEN 3
    ELSE 4
  END
