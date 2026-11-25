# Midterm rehearsal guide

Prepared narrative: **12:45**. Reserved Q&A: **2:15**. Total plan: **15:00**.
Suggested speaking split: Omar 6:15; Abdelrahman 6:30. Main slides 1–16; separate appendix slides 1–4.

| Slide | Topic | Suggested speaker | Window |
|---|---|---|---|
| 1 | Title | Omar | 00:00–00:20 |
| 2 | Problem definition | Omar | 00:20–01:20 |
| 3 | Aim & four objectives | Omar | 01:20–02:25 |
| 4 | Industrial partner | Omar | 02:25–02:50 |
| 5 | DispatchMAS | Omar | 02:50–03:50 |
| 6 | TriAgent | Omar | 03:50–04:55 |
| 7 | Block diagram | Abdelrahman | 04:55–06:15 |
| 8 | Flowchart | Abdelrahman | 06:15–07:15 |
| 9 | Specifications | Abdelrahman | 07:15–07:50 |
| 10 | Contributions | Abdelrahman | 07:50–08:35 |
| 11 | Testing | Abdelrahman | 08:35–09:40 |
| 12 | Cost estimate | Abdelrahman | 09:40–10:25 |
| 13 | Timetable | Abdelrahman | 10:25–11:25 |
| 14 | Challenges | Omar | 11:25–12:10 |
| 15 | Conclusion | Omar | 12:10–12:45 |
| 16 | Questions | Both | 12:45–15:00 |

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

DispatchMAS is our closest reference for emergency caller–dispatcher conversation. It creates 100 synthetic calls from 50 adult records. A complaint taxonomy and protocol guide caller and dispatcher agents, and four physicians review the simulated interactions. The reported 94 percent concerns contacting the correct potential auxiliary agent within the simulation. It is not a measured delivery rate to a real hospital or ambulance. Its communication experiments are English-only, the address is fixed, and responder contact is mocked. We take the focused-questioning idea, then plan separate tests for varied locations, bilingual telephone input, and receipt at a working test receiver.

Delivery cue: Define what the 94% measures before discussing the number. Point to “mocked in simulation.”

Transition: TriAgent informs a different part of the design: selecting work when information is incomplete.

### 6. Review of literature — TriAgent

TriAgent was published on 18 June 2026. It adaptively selects clinical tasks, retrieves related cases, applies safety checks, and records a critique. On 1,000 retrospective cases it reports 65.7 percent overall urgency accuracy and 85 percent critical-case recall. Those outcomes use structured clinical information and a separately trained triage classifier. The improvement cannot be attributed to agent count alone, and the same accuracy cannot be promised for a telephone symptom report. Its median runtimes are 64 seconds for the bypass and 186 seconds for the continuation path. We adopt selective task execution and reviewability, while measuring spoken-reply latency separately. Abdelrahman will now show our narrower three-agent design.

Delivery cue: Keep the two percentages tied to their own labels. Pause before the limitations. Handoff to Abdelrahman.

Transition: These studies motivate focused conversation, selective tasks, and a visible staff-review step.

### 7. Proposed system — block diagram

The thick voice arrow connects the caller and speech tools to Agent 1, the only speaking agent. Agent 2 recommends preliminary urgency and retrieves reviewed first aid. Agent 3 confirms location, checks simulated vehicle availability, travel time and equipment, and prepares the report. The three vertical double-headed arrows carry tasks and results between the agents and the Python controller. That controller is ordinary software. It maintains one record, rejects outdated results, and runs only the work affected by a change. Along the bottom, a reviewable incident reaches staff approval before transmission. The upward receipt arrow records acceptance at the test receiver. Staff can take over at any stage; receipt is separate from ambulance assignment or departure.

Delivery cue: Trace the thick voice arrow, then the three task/result arrows, then the approval and receipt paths. The agents are not a forced sequential chain.

Transition: The flowchart shows what happens when information is missing or a delivery fails.

### 8. Proposed system — flowchart

The rounded symbol starts the call. The process boxes collect facts, assess preliminary urgency and guidance, and confirm location and simulated resources. The first diamond asks whether staff approve. No returns to clarification or staff takeover; Yes sends the approved request. Delivery can use up to three attempts with the same request ID. The second diamond checks for a receipt. Yes records the receipt; No ends in an alert with unconfirmed delivery. A receipt confirms receiver acceptance, not ambulance departure.

Delivery cue: Follow the start/process symbols, explain the staff-approval diamond, then the receipt diamond. Trace the No loops and failure end explicitly.

Transition: These steps give us measurable system specifications.

### 9. System specifications

These are targets and boundaries. The 1.5-second value is the first meaningful audible response after a caller finishes a turn. A filler acknowledgment does not qualify. English, Egyptian Arabic, and mixed-language calls will be measured separately. The prototype represents one hospital and uses simulated ambulance resources. The proposed notification limit is three attempts with duplicate prevention. Urgency labels and first-aid content still require qualified review.

Delivery cue: Say “target” before the latency value. Expand p95 as the 95th percentile.

Transition: Our contribution is how these requirements connect into one workflow.

### 10. Contributions & uniqueness

We compare capabilities rather than ranking incompatible accuracy percentages. DispatchMAS evaluates synthetic conversation with a fixed address and mocked contact. TriAgent evaluates clinical information and escalation logic, without a telephone or receiver trial. Our anticipated contribution is the connection between bilingual telephone intake, corrections, confirmed location, a suitable simulated resource, and approved notification with a receipt. Every entry in our row is planned. We are not proposing a new language model or clinical triage standard, and we are not claiming that no other system has ever combined similar functions.

Delivery cue: Read across one study row, then the planned row. Emphasize the word “planned.”

Transition: We will test that contribution through the following measurements.

### 11. Proposed testing procedures

Testing starts with individual components, then connected services, then full simulated emergency calls. Annotated scenarios provide the facts we expect to collect. A qualified reviewer must agree urgency labels and guidance before testing. We will measure information errors, urgency errors, location confirmation, meaningful-reply delay, notification outcomes, and cost. We will separate transcript interpretation from end-to-end speech tests, so we can identify whether an error came from recognition or reasoning. Tests include noise, code-switching, corrected addresses, unavailable vehicles, call interruptions, and delayed or duplicate receipts. A failure is an outcome to record and explain. No clinical effectiveness or real ambulance deployment is established by these prototype tests.

Delivery cue: Explain the three table columns. Give one unit-test example and one failure/recovery example, then identify the full system test.

Transition: The following table estimates a small test budget using checked unit prices and explicit usage assumptions.

### 12. Cost analysis — estimated test budget

This estimate uses official prices checked on 24 November for 100 five-minute test calls. The model-token allowance covers all three roles. We budget live transcription and both the telephone and SIP connection legs. Speech generation and map usage fit within the stated monthly free allowances, assuming those allowances are unused. The total is 17 dollars and 78 cents before tax. Existing equipment and internet are assumed. This is a US test route; an Egyptian hospital line needs its own quote. Providers are costing candidates, and actual usage will be measured.

Delivery cue: State the test scenario, total and free-allowance assumption. Explain one row; distinguish a test-route estimate from an Egypt quote.

Transition: The remaining design work is scheduled against the confirmed submission date.

### 13. Timetable — responsibilities

The dates retain the thesis schedule through the confirmed 17 January deadline. The proposed presentation allocation gives each deliverable one accountable lead. Omar owns scope, guidance and bilingual cases, controller interfaces, location rules, evaluation scenarios and the final report. Abdelrahman owns telephone and speech, the dashboard and receiver, privacy and costing, integration review and the decision log. This is six deliverables for Omar and five for Abdelrahman; peer review still happens across the team. The parallel rows show work that can happen together. Dates and owners are proposed, with a 14–16 January correction buffer. Omar will finish with the main challenges and conclusion.

Delivery cue: Point to the Lead column and two parallel task pairs. Each row has one accountable owner. Handoff back to Omar after the confirmed deadline.

Transition: The plan also depends on resolving several technical and clinical constraints.

### 14. Limitations & challenges

The main risks are misunderstandings in noisy or mixed-language speech, missing facts or an uncertain location, and failures across connected services. The proposed controls are separate speech-versus-interpretation tests, focused clarification, explicit unknown fields, and access to staff. For late or failed service results, the controller checks whether the incident has changed and manages bounded retries with one request identifier. These are design requirements to implement and verify. Before a hospital demonstration, the team still needs authorization and qualified review of urgency criteria, first-aid sources, and test scenarios.

Delivery cue: Use “planned response” and “will test”; do not say the prototype has already solved these problems.

Transition: Our conclusion is therefore about progress, the proposed approach, and the next steps.

### 15. Conclusion

We have defined the problem, reviewed six studies, and prepared requirements and preliminary diagrams. Our proposed approach connects three agents, a Python controller, and staff approval. Next come detailed design, tool selection, clinical review, costing, implementation, and simulated-call evaluation. The contribution is a reviewable path from call to acknowledged request. Thank you; we welcome your questions.

Delivery cue: Return to the opening purpose. Stop the prepared narrative at or before 12:45.

Transition: Questions and discussion.

### 16. Thank you

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
