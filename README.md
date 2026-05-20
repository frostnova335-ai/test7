{
  "status": "success",
  "message": "Data fetched successfully",
  "timestamp": "2026-05-19T12:00:00Z",
 
  "theme": {
    "primary_color": "#0B67C2",
    "secondary_color": "#0A4F70",
    "background_color": "#F8F6F2",
    "accent_color": "#F26A21",
    "success_color": "#2D8A4E",
    "warning_color": "#D4820A",
    "danger_color": "#E84A2E"
  },
 
  "navigation": {
    "logo_text": "InsightsHub",
    "menu_items": [
      {
        "id": "search",
        "label": "Search",
        "count": "2.4M",
        "active": true
      },
      {
        "id": "saved",
        "label": "Saved Searches",
        "count": "12",
        "active": false
      },
      {
        "id": "alerts",
        "label": "Alerts",
        "count": "3",
        "active": false
      }
    ]
  },
 
  "search_section": {
    "title": "Find any conversation.",
    "subtitle": "Semantic search across millions of call transcripts — try anything in plain language.",
 
    "search_box": {
      "placeholder": "Customer angry about billing and asked to cancel subscription...",
      "button_text": "SEARCH",
      "search_type": "semantic"
    },
 
    "suggestions": [
      "calls where customer mentioned competitor",
      "repeat caller within 7 days on same issue",
      "calls where customer mention process issues",
      "calls where CSAT is less then 3",
      "calls where CES is high",
      "calls where emotion is frustrated",
      "calls where follow up is promised",
      "calls where FCR achieved"
    ]
  },
 
  "filters": {
    "date_filters": [
      "All Dates",
      "Today",
      "Last 7 Days",
      "Last 30 Days"
    ],
 
    "queue_filters": [
      "All Queues",
      "Billing",
      "Technical Support",
      "Retention"
    ],
 
    "sentiment_filters": [
      "All Sentiment",
      "Negative",
      "Neutral",
      "Positive"
    ],
 
    "outcome_filters": [
      "All Outcomes",
      "Resolved",
      "Escalated",
      "Transferred"
    ]
  },
 
  "summary_card": {
    "title": "AI Summary",
 
    "summary_text": "Found 247 matching calls using semantic analysis. Results are ranked by relevance and recency. Negative sentiment detected in 61% of matched calls.",
 
    "chips": [
      {
        "label": "61% negative sentiment",
        "type": "red"
      },
      {
        "label": "23% baseline",
        "type": "blue"
      },
      {
        "label": "247 results",
        "type": "green"
      }
    ]
  },
 
  "results": [
    {
      "call_id": "CC-2024-084721",
 
      "customer": {
        "ANI": "109221",
        "avatar_bg": "#E8D0CC",
        "avatar_text": "#C0543A"
      },
 
      "date": "Today, 09:14",
      "duration": "8m 42s",
      "queue": "Billing",
 
      "sentiment": {
        "type": "negative",
        "label": "Negative"
      },
 
      "snippet": "Customer opened with double billing complaint and became frustrated during resolution.",
 
      "tags": [
        "billing",
        "churn",
        "repeat-contact"
      ],
 
      "stats": {
        "hold_time": "2m 10s",
        "CSAT": 2.1
      },
 
      "transcript": [
        {
          "speaker": "CUST",
          "text": "I've been charged twice this month.",
          "time": "00:04",
          "emotion": "Frustrated"
        },
        {
          "speaker": "AGENT",
          "text": "Let me check your account.",
          "time": "00:10",
          "emotion": "Neutral"
        }
      ],
 
      "analysis": {
        "summary": "Agent resolved issue correctly but empathy was delayed.",
 
        "scores": {
          "empathy": 55,
          "first_call_resolution": 80,
          "compliance": 90,
          "pace": 45
        },
 
        "moments": [
          {
            "time": "00:04",
            "text": "Customer frustration detected.",
            "type": "Trigger Event"
          },
          {
            "time": "01:05",
            "text": "Duplicate transaction confirmed.",
            "type": "Key Moment"
          }
        ]
      }
    }
  ]
}
 
