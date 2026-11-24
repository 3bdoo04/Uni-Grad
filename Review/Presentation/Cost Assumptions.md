# Estimated test budget — Uni-Grad

**Official unit prices checked: 24 November 2026.** All pricing pages were retrieved successfully from the providers. The previous network restriction is resolved. This is an estimate for a stated test scenario, not a supplier quote for an Egyptian hospital or a final choice of providers.

Scenario: **100 simulated five-minute calls in one month**, in **US dollars before tax**. The model allowance covers all three agent roles together. Google monthly free allowances are assumed to be unused by other work on the billing account. Existing development equipment and internet are assumed.

| Component | Assumed usage | Checked rate | Calculation | Estimated cost | Official source |
|---|---|---|---|---:|---|
| Three language-model roles | 1M input tokens + 250k billed output tokens, including reasoning | GPT-5.4 mini, Standard tier: $0.75/M input; $4.50/M output | 1 × 0.75 + 0.25 × 4.50 = 1.875 | $1.88 | [OpenAI pricing](https://developers.openai.com/api/docs/pricing) |
| Live speech transcription | 500 minutes of live input audio | GPT-Live-Transcribe: $0.017/minute | 500 × 0.017 | $8.50 | [OpenAI live-transcription model](https://developers.openai.com/api/docs/models/gpt-live-transcribe) |
| Spoken replies | 100,000 characters | Google Chirp 3: HD: first 1M characters/month free, then $30/M | 100,000 is within the unused free allowance | $0.00 | [Google Text-to-Speech pricing](https://cloud.google.com/text-to-speech/pricing) |
| Telephone and gateway connection | 500 US local inbound minutes + 500 SIP minutes + one number/month | $0.0085/min inbound; $0.004/min SIP; $1.15/number/month | 500 × 0.0085 + 500 × 0.004 + 1.15 | $7.40 | [Twilio US voice pricing](https://www.twilio.com/en-us/voice/pricing/us) |
| Location lookup and travel time | 200 geocodes + 1,000 route-matrix elements | Geocoding and Compute Route Matrix Essentials each have 10,000 free monthly events; first paid tier $5/1,000 | Both quantities fit their unused free allowances | $0.00 | [Google Maps pricing](https://developers.google.com/maps/billing-and-pricing/pricing) |
| Backend, retrieval, storage and staff dashboard | Self-host on an existing development PC | No additional software licence charge for Python / FastAPI / LiveKit / Chroma | Existing PC and internet assumed | $0.00 | Open-source licences below |
| **Estimated scenario total** | | | **1.875 + 8.50 + 7.40 = 17.775, rounded to cents** | **$17.78** | **Before tax; unused Google free allowances assumed** |

If the Google free allowances have already been consumed by other account usage, the same quantities at the first paid tiers add $3 for speech, $1 for geocoding and $5 for route-matrix elements. That gives **about $26.78 before tax**. Free usage is conditional on the applicable account terms and remaining allowances; billing must be enabled for the Google services. Do not treat the $0 entries as unlimited free access.

The telephone example includes both the incoming public switched telephone network (PSTN) leg and a Session Initiation Protocol (SIP) leg to the self-hosted LiveKit gateway. It uses published **US test-route prices**, not Egyptian hospital-line prices or confirmation of Egyptian number availability. Alternative routing, such as Twilio Media Streams or hosted LiveKit, needs its own costing. No call-recording, Conversation Relay, external text-message, WhatsApp or actual ambulance-service charge is assumed. Approved notifications go to the self-hosted test receiver.

The previous GPT-4o mini, Whisper and tts-1 price examples were removed after the current OpenAI pages marked them deprecated. The replacement services are **costing candidates**, not final purchases or implementation decisions. Model choice, latency, language handling and clinical-information quality still require prototype tests. [Google's voice list](https://docs.cloud.google.com/text-to-speech/docs/list-voices-and-types) includes Arabic and English Chirp 3: HD voices; this does not establish Egyptian-dialect suitability or medical speech accuracy.

Actual usage may differ from these allowances. Count all model prompts, retrieved context, retries and billed reasoning/output tokens across the three roles. Audio minutes, connected call minutes, gateway minutes, generated characters, geocoding events and route-matrix elements are separate billing quantities. The budget is neither a minimum nor a cap.

Excluded: taxes, currency conversion, caller charges, Egypt routing, new hardware, internet, electricity, cloud hosting, production backups/monitoring, paid support, clinical-review labour and services outside the disclosed scenario. The backend's $0 covers additional licence charges only. No promotional credits or batch/cached-token discounts are used in the model estimate.

Licence sources:

- [FastAPI MIT licence](https://github.com/fastapi/fastapi/blob/master/LICENSE)
- [LiveKit Apache 2.0 licence](https://github.com/livekit/livekit/blob/master/LICENSE)
- [Chroma Apache 2.0 licence](https://github.com/chroma-core/chroma/blob/main/LICENSE)

The editable source bundle contains `pricing-assumptions.json`, downloaded provider pages, retrieval URLs/dates/hashes, and `pricing-sources/verified-price-facts.json`. The latter records the exact published rows used for the calculations. Older failed retrieval logs are historical evidence; they do not describe the now-active network access.
