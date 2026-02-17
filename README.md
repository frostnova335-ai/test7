
I need to create a ppt in which i have 3 slides -

1) KPi list and defination (using data below)
2) KPI analysis (using data below)
3) KPI charts (using above image)
4) Dashboard tabs and filter -(1 tab for VA insights as above, remaining 2 tabs only show the ETL data in table format )

Metric	Description 	Calculation Logic	Formula
Authentication Rate	The percentage of residential calls who got successfully authenticated through the Virtual Assistant (VA), as designed	"Successfully authenticated calls /
Total residential calls handled by the VA"	"SUM(
  CASE WHEN caller_type = 'Residential'
   AND authentication_by_va_success_flag = 1
  THEN 1 ELSE 0 END
)
/
SUM(
  CASE WHEN caller_type = 'Residential'
  THEN 1 ELSE 0 END
)"
Containment Rate	The percentage of eligible missed pickup (MPU) calls that the Virtual Assistant (VA) resolves effectively without the need for agent intervention, in line with the intended design	Successfully handled eligible MPU calls without escalation  / Total eligible MPU calls	"SUM(
  CASE
    WHEN mpu_case_closure = 1
     AND mpu_intent_identified_flag = 1
     AND mpu_eligible_flag = 'Eligible'
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN mpu_intent_identified_flag = 1
     AND mpu_eligible_flag = 'Eligible'
    THEN 1 ELSE 0
  END
)"
Live Agent Handoff Rate	The percentage of residential calls that are transferred to live agents 	Total residential calls transferred to Genesys / Total residential calls 	"SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND escalated_1 IN (
       'In Scope Live Agent Handoff',
       'Out of Scope Live Agent Handoff'
     )
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN caller_type = 'Residential'
    THEN 1 ELSE 0
  END
)"
Out of Scope Intent	The percentage of residential authenticated calls that did not relate to the missed pickup intent	(Total residential authenticated calls -  Missed PickUp intent calls) / Total residential authenticated calls 	"SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
     AND mpu_intent_identified_flag = 0
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
    THEN 1 ELSE 0
  END
)"
Avg. Handling Time (AHT)  	The average call duration of residential calls handled by the virtual assistant (VA)	Total VA call duration of residential calls / Total residential VA calls	AVG(AHT)
Intent Success Rate 	The percentage of residential MPU calls where the virtual assistant correctly identifies the MPU intent on the first attempt	Count of residential authenticated MPU calls with MPU intent identified correctly on first attempt / Total residential authenticated calls where at least one of the intents identified was MPU	"SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
     AND mpu_intent_identified_flag = 1
     AND mpu_intent_identified_1st_attempt_flag = 1
     AND here_for_mpu_flag = 1
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
     AND mpu_intent_identified_flag = 1
    THEN 1 ELSE 0
  END
)"
AI Misclassification Rate 	The percentage of residential MPU calls where the virtual assistant incorrectly identifies the caller’s intent (MPU)	Count of residential authenticated calls, not for MPU, for which at least one of the intent is identified as MPU / Total residential authenticated calls where at least one of the intents identified was MPU	"SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
     AND mpu_intent_identified_flag = 1
     AND here_for_mpu_flag = 0
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND authentication_by_va_success_flag = 1
     AND mpu_intent_identified_flag = 1
    THEN 1 ELSE 0
  END
)"
Missed Utterance Report	"The percentage of AI prompts that resulted in exception handling
- At node level"	Count of questions from AI that resulted in exception handling (includes invalid/ no customer response, abandonment, and transfer) / Total questions from AI	"SUM(number_of_ai_prompts_exception_handling)
/
SUM(number_of_question_prompts_from_ai)"
Prompt Success Rate 	The percentage of AI prompts that resulted in the desired customer response or action	Count of questions from AI that resulted in expected customer response / Total questions from AI	"SUM(number_of_successful_prompts_from_ai)
/
SUM(number_of_question_prompts_from_ai)"
Agentic AI Traffic Share 	The percentage of residential calls handled by Agentic AI	Total residential calls handled by VA and MPU module within VA / Total residential calls incoming to VA 	"SUM(
  CASE
    WHEN handled_by_agentic_ai_flag = 1
    THEN 1 ELSE 0
  END
)
/
SUM(
  CASE
    WHEN caller_type = 'Residential'
    THEN 1 ELSE 0
  END
)"
Agent Escalation Volume 	The volume of residential calls that are transferred to live agents 	Count of residential calls transferred to Genesys	"SUM(
  CASE
    WHEN caller_type = 'Residential'
     AND escalated_1 IN (
       'In Scope Live Agent Handoff',
       'Out of Scope Live Agent Handoff'
     )
    THEN 1 ELSE 0
  END
)"
Number of retries (Customer Verification)	1. Count of residential calls where customer verification was re-attempted.	1. Number of residential calls where authentication was re-attempted	 COUNT(*) WHERE retry_of_authentication_flag = 1 AND caller_type = 'Residential'
Number of retries (MPU)	2. Count of residential authenticated calls where Missed PickUp resolution was re-attempted.	2. Number of residential authenticated MPU calls where MPU resolution prompt(s) were re-attempted	"COUNT(
  CASE
    WHEN retry_of_mpu_flag = 1
     AND caller_type = 'Residential'
    THEN 1
  END
)"
Abandonment Rate	"The percentage of residential calls that got abandoned by the customer while talking to VA, before the issue is resolved.
1. Based on the journey step 
       a. Auth completed  
            i. ANI based Auth
            ii. Address Match
       b. Missed pickup 
            i. intent captured
            ii. reason for missed pickup provided
            iii. Eligibility for raising missed pickup request confirmed
            iv. Missed pickup request raised
2. Based on the length of conversation  
       a. 0 - 5 seconds
       b. 5 - 30 seconds
       c. 30 seconds plus"	"Overall: Count of residential calls that got abandoned by the customer while talking to VA, before the issue is resolved / Total number of residential calls

By journey step:
Count of residential calls that got abandoned by the customer with last completed being X (e.g., ANI based Auth) / Total number of residential calls

By length of conversation:
Count of residential calls that got abondoned by the customer while talking to VA, before the issue is resolved, with length of conversation being X (e.g., 0-5 secs) / Total number of residential calls"	"SUM( CASE WHEN abandonment_by_customer_flag = '1' THEN 1 ELSE 0 END )
      /
      SUM( CASE WHEN caller_type = 'Residential' THEN 1 ELSE 0 END )
    )"
Peak hours and traffic handled by AI vs. Agents	"Avg count of calls at half-hourly intervals for:
1. Incoming calls to VA
2. Incoming calls to VA which got escalated"	"Avg count of calls at half-hourly intervals for:
1. Incoming calls to VA
2. Incoming calls to VA which got escalated to Genesys"	"( SUM(escalated_rows) / SUM(total_rows) ) * 100
 
Where 
escalated_rows = COUNT( CASE WHEN escalated = 'true' THEN 1 ELSE 0 END )
total_rows     = COUNT(*)
 "
			

