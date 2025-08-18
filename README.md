PA Status
Numerator: Chats on pa_status / plan_number / eligibility+Plan Message that end cleanly (AMELIA_HANDLED, CALLER_HANGUP, or “Yes”) without any disqualifiers.
Denominator: All chats on pa_status / plan_number / eligibility+Plan Message (regardless of outcome).
Complete/Submit a Form
Numerator: Document/form subflows (Upload Documents / Update Answers / Edit Drug details or selecting fax numbers) where specific action/result keywords appear.
Denominator: All chats with edit_or_submit_form or fax_help intent.
Archive/Unarchive
Numerator: Archive/Unarchive subflows that show handled/success signals (e.g., AMELIA_HANDLED, archived/unarchived confirmations, 200 response, “Archive User Able” without escalation), including the Cancel Request → Archive path.
Denominator: All chats about archiving/unarchiving (intents) or the Cancel Request + Archive path.
Eligibility
Numerator: eligibility chats that hit any troubleshooting success/failure milestones listed.
Denominator: All eligibility chats excluding those that went through Eligibility – Plan Message.
Convert to Classic
Numerator: convert_to_classic intent with a concrete outcome (already classic, conversion success, agent needed, plan/form not eligible).
Denominator: All chats with convert_to_classic intent.
Account Match
Numerator: account_match_help with either “why question” or “Prescriber verification” subflows.
Denominator: account_match_help where the user did not go back to Main Menu.
Authentication Flow
Numerator: Authentication flow reached and user was able to log in.
Denominator: Any chat that entered the Authentication flow.
Cancel Request
Numerator: Delete-request subflow completed without the “Users not able to delete” error.
Denominator: Any chat that entered the Cancel Request subflow.
Overall Deflection
Numerator/Denominator: Uses Total chats as the base volume for overall rate calculations.
