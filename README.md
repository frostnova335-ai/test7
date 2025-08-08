SELECT
  DATE("created") AS date,
  COUNT(*) AS total_chats,
  SUM(CASE WHEN "escalated" = TRUE THEN 1 ELSE 0 END) AS live_agent_handoffs,
  ROUND(
    100.0 * SUM(CASE WHEN "escalated" = TRUE THEN 1 ELSE 0 END) / COUNT(*),
    2
  ) AS live_agent_handoff_rate
FROM public."YourTableName"
GROUP BY DATE("created")
ORDER BY DATE("created") ASC
