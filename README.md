{
  "request": {
      "search_text": "repeat caller within 7 days on same issue",
      "session_id": "SESSION-9834834",
      "user_id": "admin",
      "call_id": "CC-2024-084721", //optional param
      "timestamp": "2026-05-21T15:16:00Z"
  },

  "response": {
    "search": {
      "query": "repeat caller within 7 days on same issue",

      "total_results": 247,

      "search_time_ms": 1320
    },

    "suggestions": [
      "calls where customer mentioned competitor",
      "repeat caller within 7 days on same issue",
      "calls where customer mention process issues",
      "calls where CSAT is less than 3",
      "calls where CES is high",
      "calls where emotion is frustrated"
    ],

    "quick_filters": [
      {
        "label": "Negative",
        "count": 61
      },
      {
        "label": "Escalation",
        "count": 14
      },
      {
        "label": "Compliance",
        "count": 9
      },
      {
        "label": "Repeat Contact",
        "count": 22
      }
    ],

    "todays_pulse": {
      "calls_processed": 1847,

      "calls_change_percent": 12,

      "negative_sentiment_rate": 23,

      "negative_sentiment_change": 4,

      "first_call_resolution": 68,

      "fcr_change": -2,

      "alerts": [
        "billing spike",
        "investigate"
      ]
    },

    "filters_available": {
      "date_ranges": [
        "today",
        "last_7_days",
        "last_30_days",
        "all_dates"
      ],

      "queues": [
        "Billing",
        "Retention",
        "Technical Support",
        "Customer Care"
      ],

      "sentiments": [
        "positive",
        "neutral",
        "negative"
      ],

      "outcomes": [
        "Resolved",
        "churn",
        "escalation",
        "repeat-contact"
      ]
    },

    "ai_summary": {
      "title": "AI SUMMARY",

      "summary_text": "Found 247 matching calls using semantic analysis. Results are ranked by relevance and recency. Negative sentiment detected in 61% of matched calls — significantly above the 23% baseline. Top themes: billing errors, account access issues, and cancellation intent.",

      "metrics": [
        {
          "label": "61% negative sentiment",
          "type": "negative"
        },
        {
          "label": "23% baseline",
          "type": "baseline"
        },
        {
          "label": "247 results",
          "type": "results"
        }
      ]
    },

    "interactions": [
      {
        "call_id": "CC-2024-084721",

        "customer_initials": "MT",

        "customer_name": "Marcus T.",

        "queue": "Billing",

        "timestamp": "2026-05-21T09:14:00Z",

        "duration": "8m 42s",

        "hold_time": "2m 10s",

        "transfers": 1,

        "csat": 2.1,

        "sentiment": "negative",

        "summary": "Customer opened with 'I've been charged twice this month and I want an explanation now.' Agent attempted to look up account but struggled with system slowness. Customer became increasingly frustrated saying they'd been loyal for 6 years and this was unacceptable. Agent offered £10 credit but customer rejected it.",

        "tags": [
          "billing",
          "churn",
          "repeat-contact"
        ],

        "detail_panel": {
          "active_tab": "transcript",

          "tabs": [
            "transcript",
            "analysis",
            "moments"
          ],

          "transcript": [
            {
              "speaker": "CUST",
              "time": "00:04",
              "message": "Hi, I've been charged twice this month and I need someone to explain this right now.",

              "sentiment": "frustrated"
            },
            {
              "speaker": "AGENT",
              "time": "00:11",
              "message": "I completely understand your concern. Let me pull up your account right away. Can I take your account number or postcode to verify?",

              "sentiment": "neutral"
            }
          ],

          "analysis": {
            "conversation_summary": "Customer was frustrated due to duplicate billing charges. Agent followed process correctly but delayed empathy and resolution.",

            "quality_scores": {
              "empathy": 55,
              "compliance": 90,
              "pace": 45,
              "fcr": 80
            },

            "detected_topics": [
              "duplicate billing",
              "customer frustration",
              "retention risk"
            ]
          },

          "moments": [
            {
              "time": "00:04",
              "type": "Trigger Event",
              "text": "Customer frustration detected."
            },
            {
              "time": "01:05",
              "type": "Key Moment",
              "text": "Duplicate transaction confirmed."
            },
            {
              "time": "03:42",
              "type": "Escalation Risk",
              "text": "Customer threatened cancellation."
            }
          ]
        }
      }
    ]
  }
}
