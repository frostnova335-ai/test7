1) Key Discussion Points & Clarifications

1.1 Data dictionary & column semantics
A formal data dictionary is needed to define columns (e.g., authentication success, retry flags, abandoned by customer, stage completed before abandonment, failure reason codes).
Retry flags:
Retry of Authentication is binary (1 = some retry occurred within authentication; 0 = none).
Auth Retry Prompt shows where the retry happened (e.g., “Phone verification”; ideally lists both if retries occurred at phone and address; current behavior may show only one — to be verified).
MPU eligible flag: can be blank if customer is eligible for multiple service requests and does not pick one in the flow.
1.2 How to analyze exports (bottom‑of‑funnel approach)
Start with outcomes: Authenticated, Escalated, Abandoned.
Use Stage Completed Before Abandonment to locate friction points (e.g., phone verification, address verification, MPU).
Then narrow by reason codes (R1/R2/R3) and triage calls for deeper review.
1.3 Failure reason codes (R1/R2/R3)
There is a conflicting understanding of R‑codes:
One view: R1 = Account inactive, R2 = Service interrupt, R3 = Container inactive.
Another view (from the sheet): R3 = Phone verification failure.
Action: reconcile R‑code mapping in the data dictionary and reflect the same mapping in exports + dashboard.
1.4 Practical walk‑through (Dec 19 test, 51 residential calls)
Filter unauthenticated calls; examine R3 (phone number not verified) subset.
Use abandonment columns (not just Stage Completed) to confirm whether calls abandoned vs moved ahead.
Realization: Phone number failure should not always block address verification; opportunity to increase progression to address verification when phone match fails.
1.5 Looping & bulk intent
Example highlighted where bulk intent flowed into MPU, resulting in looping; escalation occurred.
Data view didn’t clearly expose repeated bulk intent utterances; opportunity to improve loop/ambiguity flags or prompt reasons to make such issues visible without call listening.
1.6 Dashboard adjustments
Containment rate (VA) shown as 100% prompted concern; proposal to rename/clarify the operational definition.
Re‑order top‑line metrics sequentially (e.g., Calls → Authentication success → MPU progression/case creation → Escalation/Abandonment).
1.7 Operational notes
VDI vs public ID for meetings/screenshare caused copy/paste issues; team agreed to join from public ID going forward to avoid interruptions.
Google call drops may skew abandonment; continue working with provider; annotate this in analysis as a known technical factor.
