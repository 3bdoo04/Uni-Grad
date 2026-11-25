# Midterm rehearsal guide

Prepared narrative: **12:45**. Reserved Q&A: **2:15**. Total plan: **15:00**.
Suggested speaking split: Omar 6:15; Abdelrahman 6:30. Main slides 1–17; separate appendix slides 1–4.

| Slide | Topic | Suggested speaker | Window |
|---|---|---|---|
| 1 | Title | Omar | 00:00–00:20 |
| 2 | Problem definition | Omar | 00:20–01:20 |
| 3 | Aim & four objectives | Omar | 01:20–02:25 |
| 4 | Industrial partner | Omar | 02:25–02:50 |
| 5 | DispatchMAS | Omar | 02:50–03:50 |
| 6 | TriAgent | Omar | 03:50–04:55 |
| 7 | Block diagram | Abdelrahman | 04:55–06:05 |
| 8 | Flowchart | Abdelrahman | 06:05–06:50 |
| 9 | Animated call example | Abdelrahman | 06:50–07:35 |
| 10 | Specifications | Abdelrahman | 07:35–08:05 |
| 11 | Contributions | Abdelrahman | 08:05–08:45 |
| 12 | Testing | Abdelrahman | 08:45–09:40 |
| 13 | Cost estimate | Abdelrahman | 09:40–10:25 |
| 14 | Timetable | Abdelrahman | 10:25–11:25 |
| 15 | Challenges | Omar | 11:25–12:10 |
| 16 | Conclusion | Omar | 12:10–12:45 |
| 17 | Questions | Both | 12:45–15:00 |

## Objective pairing

1+8: bilingual voice and cost; 2+7: reliable incident record; 3+4: triage/guidance/location; 5+6: resources and approved notification.

## Speaking notes

### 1. Agentic Emergency Tele-Triage & Autonomous Medical Dispatch System

Every emergency call needs clear patient facts, a confirmed location, and a request that someone actually receives. Our project connects these steps through three agents and a hospital-reviewed workflow.

Delivery cue: Open with the purpose. Do not read the full title or every logo. Pause after “actually receives.”

Transition: First, what makes that connection difficult?

### 2. Problem definition

Our main problem is turning an emergency call into enough reliable information for an urgency assessment and an ambulance decision. First, callers may omit symptoms or details about breathing and consciousness. A serious case can therefore be hard to recognise from the description alone. Second, help needs a confirmed location and a suitable available vehicle, with the needed equipment and a reasonable travel time. Third, the dispatch request must reach the receiving team, and the incident must show whether delivery was confirmed. These are the workflow risks our prototype will address and test; they are not claims about failure rates at a particular hospital.

Delivery cue: Explain the main statement, then each row as a problem and its consequence. Use one caller example; keep implementation details for the design slides.

Transition: Our aim and four objectives show how the prototype will address these problems.

### 3. Project aim & objectives

Our aim is to develop and evaluate a hospital telephone prototype for preliminary triage and staff-approved ambulance dispatch in English and Egyptian Arabic. Four paired objectives turn that aim into work we can test. First, provide bilingual voice interaction and measure meaningful-reply delay, language performance and cost. Second, preserve patient facts and corrections through interruptions and reject outdated results. Third, recommend preliminary urgency and reviewed first aid, then confirm the caller’s location. Fourth, match a simulated ambulance using availability, travel time and equipment, obtain staff approval, and verify request delivery with failure and duplicate tests. The 1.5-second value remains a target, not a result.

Delivery cue: State the aim once, then spend about 12 seconds per objective. Bold blue names the objective, regular blue describes the work, and green identifies its evaluation.

Transition: Clinical review and realistic requirements will need input from an industrial partner.

### 4. Industrial partner

The thesis reports outreach to these organizations, but no official partner has been secured. We need practical requirements, qualified review of urgency and first-aid material, and an authorized test telephone arrangement. Outreach is not evidence of a partnership or access to patient records.

Delivery cue: Be precise about status. Do not imply that any listed organization endorses the prototype.

Transition: Two of the reviewed studies most directly inform our proposed workflow.

### 5. Review of literature — DispatchMAS

DispatchMAS tests emergency medical conversations. A caller agent describes an emergency; a dispatcher agent asks focused questions and gives advice. Four doctors review 100 simulated calls from 50 patient records. Advice was provided in 91 percent of scenarios where it was needed. This measures whether advice was given, not whether every instruction was medically correct. Most physician ratings of helpfulness were four or five out of five. Tests use English, one fixed address and simulated responders; live telephone speech is not tested. Its relevance is the shared patient-facing function: collecting symptoms during an emergency call and providing medical guidance before an ambulance arrives. TriAgent focuses on the assessment behind that conversation.

Delivery cue: Explain 91% as advice provision in simulated scenarios needing advice. Then state the shared function: symptom questioning and medical guidance before ambulance arrival.

Transition: TriAgent addresses urgency assessment when the patient description is incomplete.

### 6. Review of literature — TriAgent

TriAgent handles incomplete patient information. The Orchestrator Agent selects specialist tasks. A trained urgency model uses symptoms and vital signs; other modules retrieve similar cases, draft a care plan and check drug and allergy risks. The Critique Agent reviews the plan and requests corrections. Critical presentations bypass that review for immediate escalation. Across 1,000 recorded cases, 65.7 percent received the correct urgency level. Among reference-critical cases, 85 percent were identified as critical. These are different denominators. Typical case processing exceeded one minute; live calls were not tested. The shared aspect is coordinated specialist roles that turn incomplete patient information into an urgency recommendation. Our project does not prescribe medication. Abdelrahman will show our design.

Delivery cue: Explain the roles in order: Orchestrator selects; specialist modules assess, retrieve, plan and check; Critique reviews. Distinguish overall accuracy from critical-case recall. End with the shared medical assessment function.

Transition: Our narrower design uses three language-model roles and a Python controller.

### 7. Proposed system — block diagram

Start with the caller and speech tools. They convert audio to text and reply text back to speech. Click the arrow, then Agent 1: it collects symptoms and addresses, asks questions and retains corrections. The next arrow leads to ordinary Python software, which stores the case, runs agents when facts change and rejects outdated results. Its lower branches are separate tasks, not an agent chain. Agent 2 suggests urgency using reviewed first aid. Agent 3 confirms location and recommends a simulated ambulance using travel time, availability and equipment, then writes the report. The reviewer approves, corrects or takes over. Only approved requests reach the software receiver, which stores and confirms delivery. The controller retries at most three times with the same ID and alerts the reviewer if confirmation is missing.

Delivery cue: Use 13 clicks: block, arrow, next block. After the controller, reveal each branch arrow before its destination block. The legend explains navy transcript/reply text, gray dashed agent work/results and green hospital messages. Speak through the diagram within the existing 70-second slot.

Transition: The flowchart shows the approval and delivery decisions in more detail.

### 8. Proposed system — flowchart

The rounded symbol starts the call. The process boxes collect facts, assess preliminary urgency and guidance, and confirm location and simulated resources. The first diamond asks whether staff approve. No returns to clarification or staff takeover; Yes sends the approved request. Delivery can use up to three attempts with the same request ID. The second diamond checks for a receipt. Yes records the receipt; No ends in an alert with unconfirmed delivery. A receipt confirms receiver acceptance, not ambulance departure.

Delivery cue: Follow the start/process symbols, explain the staff-approval diamond, then the receipt diamond. Trace the No loops and failure end explicitly.

Transition: Here is one fictional call following those steps.

### 9. An example emergency call

This is a proposed example, not a live prototype result. Click one: the caller says in Egyptian Arabic that their father is dizzy and needs help. Click two: the conversation collects symptoms, checks consciousness and breathing, and confirms the address. Click three: the urgency recommendation goes to staff, with an available simulated vehicle; the eight-minute estimate is an assumption. Click four: staff review and approve request 042. Click five: our test receiver confirms arrival of that request, and the incident records delivery. The animation shows the intended workflow. Delivery confirmation is separate from ambulance departure.

Delivery cue: Use Slide Show mode. Click once per step and explain the newly revealed panel. Five 350-millisecond fades are controlled by the presenter; the slide never advances automatically.

Transition: We will measure these steps against the following system targets.

### 10. System specifications

These are targets and boundaries. The 1.5-second value is the first meaningful audible response after a caller finishes a turn. A filler acknowledgment does not qualify. English, Egyptian Arabic, and mixed-language calls will be measured separately. The prototype represents one hospital and uses simulated ambulance resources. The proposed notification limit is three attempts with duplicate prevention. Urgency labels and first-aid content still require qualified review.

Delivery cue: Say “target” before the latency value. Expand p95 as the 95th percentile.

Transition: Our contribution is how these requirements connect into one workflow.

### 11. Contributions & uniqueness

Section 1.5 proposes four contributions. TriAgent has no live-call correction tests; our controller will update affected tasks without restarting the interview. DispatchMAS tests English; we propose English and Egyptian Arabic, separating speech from interpretation errors. Its fixed address leaves varied locations untested; we will explain the confirmed address and simulated ambulance choice, showing missing facts. Its responder contact is simulated; we will verify approved request delivery, prevent duplicates and alert staff on failure. Our distinction is connecting these functions in one prototype. These are planned contributions.

Delivery cue: Use four clicks in reading order: top left, top right, bottom left, bottom right. Spend about nine seconds per card, then emphasize the shared workflow. Say planned; do not claim improved clinical outcomes.

Transition: We will test these contributions through the following procedures.

### 12. Proposed testing procedures

Each test has a specific input and expected check. First, compare urgency and first aid with clinician-reviewed answers, counting missed Red cases. Second, change Building 12 to 21 and delay the Building 12 map response: it must not overwrite the corrected location. Third, make ambulance A busy, B missing equipment and C suitable: select C, or alert staff when C is removed. Fourth, replay English, Egyptian Arabic and mixed calls, checking facts and measuring the first meaningful reply. Fifth, test a second-attempt confirmation, three failed attempts and a lost confirmation: stop retries, alert staff and prevent duplicates. Finally, try sending before reviewer approval: nothing is sent. Obtain approval, then send the approved request.

Delivery cue: Reveal the six rows in order with six clicks. Point to the action and expected output in the last column. Allow about eight seconds per row plus a short introduction. The first meaningful reply has a target below 1.5 seconds, not a measured result.

Transition: The following table estimates the cost of running a small test programme.

### 13. Cost analysis — estimated test budget

This estimate uses official prices checked on 24 November for 100 five-minute test calls. The model-token allowance covers all three roles. We budget live transcription and both the telephone and SIP connection legs. Speech generation and map usage fit within the stated monthly free allowances, assuming those allowances are unused. The total is 17 dollars and 78 cents before tax. Existing equipment and internet are assumed. This is a US test route; an Egyptian hospital line needs its own quote. Providers are costing candidates, and actual usage will be measured.

Delivery cue: State the test scenario, total and free-allowance assumption. Explain one row; distinguish a test-route estimate from an Egypt quote.

Transition: The remaining design work is scheduled against the confirmed submission date.

### 14. Timetable — responsibilities

The dates retain the thesis schedule through the confirmed 17 January deadline. The proposed presentation allocation gives each deliverable one accountable lead. Omar owns scope, guidance and bilingual cases, controller interfaces, location rules, evaluation scenarios and the final report. Abdelrahman owns telephone and speech, the dashboard and receiver, privacy and costing, integration review and the decision log. This is six deliverables for Omar and five for Abdelrahman; peer review still happens across the team. The parallel rows show work that can happen together. Dates and owners are proposed, with a 14–16 January correction buffer. Omar will finish with the main challenges and conclusion.

Delivery cue: Point to the Lead column and two parallel task pairs. Each row has one accountable owner. Handoff back to Omar after the confirmed deadline.

Transition: The plan also depends on resolving several technical and clinical constraints.

### 15. Limitations & challenges

The main risks are misunderstandings in noisy or mixed-language speech, missing facts or an uncertain location, and failures across connected services. The proposed controls are separate speech-versus-interpretation tests, focused clarification, explicit unknown fields, and access to staff. For late or failed service results, the controller checks whether the incident has changed and manages bounded retries with one request identifier. These are design requirements to implement and verify. Before a hospital demonstration, the team still needs authorization and qualified review of urgency criteria, first-aid sources, and test scenarios.

Delivery cue: Use “planned response” and “will test”; do not say the prototype has already solved these problems.

Transition: Our conclusion is therefore about progress, the proposed approach, and the next steps.

### 16. Conclusion

We have defined the problem, reviewed six studies, and prepared requirements and preliminary diagrams. Our proposed approach connects three agents, a Python controller, and staff approval. Next come detailed design, tool selection, clinical review, costing, implementation, and simulated-call evaluation. The contribution is a reviewable path from call to acknowledged request. Thank you; we welcome your questions.

Delivery cue: Return to the opening purpose. Stop the prepared narrative at or before 12:45.

Transition: Questions and discussion.

### 17. Thank you

This slide starts the question period. The planned talk ends at 12:45, leaving 2:15 inside the 15-minute maximum. Keep answers focused and open the separate appendix only when it helps. If questions are handled separately by the committee, the prepared talk still remains below the limit.

Delivery cue: Listen fully. Let the presenter responsible for a topic answer first, then add only missing information. State uncertainty honestly.

Transition:

## Q&A preparation

### Why three agents and a Python controller?

Three roles separate conversation, preliminary assessment/guidance, and coordination. Ordinary Python software maintains state and enforces approval and notification rules. Agent count alone is not claimed to improve performance.

### Is this a diagnostic or autonomous ambulance service?

No definitive diagnosis or medication prescribing is in scope. Urgency is preliminary; guidance needs qualified review. Staff can take over and must approve dispatch requests. Ambulance resources are simulated.

### What happens when a caller corrects an address?

The incident is updated, relevant work is rerun, and results tied to outdated information are rejected. The earlier statement remains available for review.

### Can you automatically obtain GPS from an ordinary call?

No. Collect an address or landmark, or use an optional location-sharing link with caller permission where supported. Confirm it with the caller and retain unresolved details.

### What does the 1.5-second target measure?

End of the caller’s turn to the first meaningful audible reply. A filler acknowledgment does not qualify. Report preparation and delivery use separate clocks; report median and 95th percentile.

### Does a delivery receipt prove that an ambulance departed?

No. Approval, sending, receiver acceptance, simulated assignment and departure are separate states and timestamps. Retry the same request ID and alert staff when delivery remains failed or unconfirmed.

### Will you compare three agents with one agent?

A separate implemented single-agent baseline is not in the current committed scope. We plan component/integration and simulated-call evaluation. Published baselines provide context under different test conditions.

### Is an industrial partner secured?

The thesis reports outreach, not a confirmed partnership. Requirements input, a test telephone route, and qualified medical review remain prerequisites.

### What does the $17.78 estimate cover?

A month with 100 five-minute US test calls, model usage across three roles, live transcription, speech generation, both telephone/gateway legs, geocoding and route-matrix usage. Official prices were checked on 24 November 2026. The total assumes unused Google free caps and existing equipment/internet; without those caps, the same quantities at first paid tiers are about $26.78 before tax. An Egyptian hospital route needs a separate quote.

### Have you published either reviewed paper?

No such project publication is reported in the thesis. DispatchMAS and TriAgent are prior research by their named authors, included for literature review.
