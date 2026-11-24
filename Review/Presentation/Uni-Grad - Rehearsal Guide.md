# Midterm rehearsal guide

Prepared narrative: **12:45**. Reserved Q&A: **2:15**. Total plan: **15:00**.
Suggested speaking split: Omar 6:15; Abdelrahman 6:30. Main slides 1–16; hidden backups 17–20.

| Slide | Topic | Suggested speaker | Window |
|---|---|---|---|
| 1 | Title | Omar | 00:00–00:20 |
| 2 | Problem & aim | Omar | 00:20–01:25 |
| 3 | Four objectives | Omar | 01:25–02:25 |
| 4 | Industrial partner | Omar | 02:25–02:50 |
| 5 | DispatchMAS | Omar | 02:50–03:50 |
| 6 | TriAgent | Omar | 03:50–04:55 |
| 7 | Block diagram | Abdelrahman | 04:55–06:25 |
| 8 | Call flow | Abdelrahman | 06:25–07:25 |
| 9 | Specifications | Abdelrahman | 07:25–08:05 |
| 10 | Contributions | Abdelrahman | 08:05–08:50 |
| 11 | Testing | Abdelrahman | 08:50–09:55 |
| 12 | Cost planning | Abdelrahman | 09:55–10:25 |
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

### 2. Problem definition & aim

The problem is the transfer from an incomplete conversation to a request that hospital staff can review. A caller may correct symptoms or an address. The system must update what it knows rather than continue using the old answer. Location is a separate issue: an ordinary telephone call does not automatically give us GPS coordinates. Finally, generating or sending an alert is different from confirming that a receiver accepted it. Our aim is to connect information collection, preliminary urgency, caller-confirmed location, and approved notification in English and Egyptian Arabic. The prototype represents one hospital and uses simulated ambulance resources.

Delivery cue: Move left to right across the three cards, then point to the aim. Explain GPS as location coordinates if asked.

Transition: We express that aim through four measurable objectives.

### 3. Project objectives

We have combined the eight thesis objectives into four without dropping any. First, provide bilingual voice interaction and measure response time, language performance, and service cost. Second, preserve one incident record through corrections, interruptions, and delayed results. Third, combine preliminary triage and reviewed first-aid guidance with caller-confirmed location. Fourth, recommend a suitable simulated ambulance and send only a staff-approved request, with receipts and duplicate prevention. Each objective has an observable test. The 1.5-second value is a design target for the first meaningful audible reply, not a result and not the time to finish the whole report.

Delivery cue: Use about 15 seconds per card. Do not read all the supporting text.

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

The caller enters through the hospital test telephone connection and speech services. Agent 1 is the only agent that speaks. It gathers facts and corrections. Agent 2 uses the current facts to recommend preliminary urgency and retrieve reviewed first-aid material. Agent 3 confirms location, checks simulated vehicle availability, estimated travel time and equipment, and prepares the report. The Python controller is not a fourth AI agent. It decides which task needs to run, validates results, and maintains one incident record. A result based on an old address must not overwrite a correction. The controller does not invoke every agent after every utterance. Staff can inspect partial information, take over the call, and approve or reject the request. Only an approved request reaches the test receiver. The receipt is logged separately from simulated assignment or departure. The diagram is simplified for the slide; the thesis contains the fuller block diagram and flowchart.

Delivery cue: Trace the caller-to-Agent-1 arrow, then each role, then the controller bar, then the bottom approval path. Do not present the three agents as a forced sequential chain.

Transition: The flowchart shows what happens when information is missing or a delivery fails.

### 8. Proposed system — call flow

The main path is collection, preliminary assessment, location and resource confirmation, and staff review. If staff approve, the controller sends the request to the test receiver. Failed delivery uses a proposed maximum of three attempts, with the same request identifier so that a retry cannot become a second order. A missing receipt produces a failed or unconfirmed state and an alert to staff. It is not silently treated as success. If the caller corrects a symptom or location, or staff reject the report, we update the incident and repeat only the affected task. Human takeover remains available throughout the call.

Delivery cue: Follow the top row left-to-right, then the lower row right-to-left. Point to the correction bar last.

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

Delivery cue: Describe the test strategy first, then highlight two measures rather than reading six cards.

Transition: Cost is part of the evaluation, but service prices have not yet been selected.

### 12. Cost analysis — planned method

Detailed costing follows service selection. We will log telephone time, speech processing, model usage, mapping, storage and notification attempts, including failures. This supports a cost per completed or failed call. No service rates or prototype total are agreed yet, and the reviewed papers do not provide directly comparable per-call costs.

Delivery cue: Explain the cost drivers. Do not invent dollar values to fill the template.

Transition: The remaining design work is scheduled against the confirmed submission date.

### 13. Timetable — remaining Grad I work

The thesis plan runs from 23 November to the confirmed 17 January Grad I deadline. These are proposed dates and leads, not claims that every task has been completed. The review and preliminary design already exist in the thesis. Omar leads guidance and bilingual scenarios, then controller interfaces and location rules. Abdelrahman leads telephone feasibility, dashboard and receiver design, and privacy and costing. Both contribute to integration review and submission. The chart groups parallel tasks for readability; the thesis retains all eleven tasks and their dependencies. Report work continues throughout, with a 14–16 January correction buffer. Omar will finish with the main challenges and next steps.

Delivery cue: Point to the deadline, two parallel work periods, and the final buffer. Handoff back to Omar.

Transition: The plan also depends on resolving several technical and clinical constraints.

### 14. Limitations & challenges

The main risks are misunderstandings in noisy or mixed-language speech, missing facts or an uncertain location, and failures across connected services. The proposed controls are separate speech-versus-interpretation tests, focused clarification, explicit unknown fields, and access to staff. For late or failed service results, the controller checks whether the incident has changed and manages bounded retries with one request identifier. These are design requirements to implement and verify. Before a hospital demonstration, the team still needs authorization and qualified review of urgency criteria, first-aid sources, and test scenarios.

Delivery cue: Use “planned response” and “will test”; do not say the prototype has already solved these problems.

Transition: Our conclusion is therefore about progress, the proposed approach, and the next steps.

### 15. Conclusion

We have defined the problem, reviewed six studies, and prepared requirements and preliminary diagrams. Our proposed approach connects three agents, a Python controller, and staff approval. Next come detailed design, tool selection, clinical review, costing, implementation, and simulated-call evaluation. The contribution is a reviewable path from call to acknowledged request. Thank you; we welcome your questions.

Delivery cue: Return to the opening purpose. Stop the prepared narrative at or before 12:45.

Transition: Questions and discussion.

### 16. Questions & discussion

This slide starts the question period. The planned talk ends at 12:45, leaving 2:15 inside the 15-minute maximum. Keep answers focused and use a backup slide only when it helps. If questions are handled separately by the committee, the prepared talk still remains below the limit.

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

### Why is there no numerical budget or measured system result?

The thesis documents preliminary design. Detailed costing follows tool selection. Implementation, clinical-label review, and simulation-based evaluation are next work; values should not be invented.

### Have you published either reviewed paper?

No such project publication is reported in the thesis. DispatchMAS and TriAgent are prior research by their named authors, included for literature review.
