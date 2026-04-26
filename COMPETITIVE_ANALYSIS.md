# Austin Service Guide — Competitive Analysis & Innovation Roadmap

**Project:** Austin Service Guide
**Date:** April 23, 2026
**Version:** 1.0
**Status:** Draft

---

## 1. Landscape Audit: What Exists Today

### 1.1 U.S. City Service Portals

**ACCESS NYC (New York City)**

- 80+ programs, 40+ screened for eligibility in a 10-step flow
- 11 human-translated languages
- No account required, minimal data collection
- Built on Drools Business Rules Management System
- Published Benefits Screening API for third-party integration
- _Limitations:_ No AI matching, no conversational interface, no mapping, no risk assessment, no proactive recommendations. NYC programs only.

**MyLA311 (Los Angeles)**

- 1,500+ services via call center, web, and mobile app
- Pin-drop location (no exact address needed for service requests)
- Photo-verified resolution confirmations
- 224 languages via AI translation
- _Limitations:_ 311 service requests only — not a social services navigator. No eligibility screening, no personalization.

**Denver "Sunny" (Citibot-powered)**

- AI chatbot handling ~20% of all 311 interactions
- 95,000+ residents engaged, 90% satisfaction
- 72 languages, 24/7 availability
- Enabled 45% reduction in live agent staffing
- _Limitations:_ Chatbot only — answers questions and files service requests. No eligibility screening, no personalized service directory, no case tracking. Route Fifty testing found it routes homelessness questions to service requests (problematic policy framing).

**BOS:311 (Boston)**

- Photo documentation of completed work (filled potholes, etc.)
- Shows the crew who did the work alongside the completed result
- 10 languages
- _Limitations:_ 311 service requests only. No social services integration.

**CHI311 (Chicago)**

- Neighborhood-level request visibility, completion estimates
- 2.3 million requests annually
- _Limitations:_ Inspector General audit (Feb 2026) found it's a "black hole" — requests coded "completed" when problems are unresolved, no transparency on process or timeframes, system "fosters distrust of government."

**SF.gov (San Francisco)**

- Design-forward approach: information organized by how people live, not how government is structured
- Custom design system ("Maya") with WCAG AA+ compliance
- Developed with input from 250+ residents
- _Limitations:_ Informational website — not an interactive service matcher.

### 1.2 International Gold Standards

**LifeSG (Singapore)**

- 100+ government services organized by life milestones (birth, housing, career, healthcare)
- 1.5M+ users
- Proactively presents services users may not have considered
- Strategic National Project under Smart Nation
- _Limitations:_ Government services only (no nonprofit integration). No conversational AI intake. Requires national digital identity.

**TAMM 3.0 (Abu Dhabi)**

- 1,000+ services from 90+ providers through a unified portal
- Multi-agent AI architecture (LangChain/LangGraph + Azure OpenAI + JAIS Arabic LLM)
- Personal AI assistant that learns user needs
- Journey-focused approach mapping life events to services
- _Limitations:_ Not open-source or transferable. Built for a different governance model (centralized emirate). Not designed for the fragmented U.S. service landscape.

**e-Estonia**

- 99% of public services online, 100% digitalization achieved December 2024
- "Once-only" data principle — provide info once, reused across systems
- All data access logged; citizens can audit who viewed their records
- Proactive services: birth triggers automatic benefit enrollment
- _Limitations:_ Decades of national-level investment. Not replicable at city level without federal infrastructure.

### 1.3 Benefits Platforms (Not City-Run)

**findhelp.org (formerly Aunt Bertha)**

- 85 million users, ~1 million program locations
- End-to-end enrollment (eligibility + application + submission + recertification)
- Austin-founded; powers ConnectATX.org with United Way
- _Limitations:_ Directory model — no AI-powered personalization, no conversational intake, no risk assessment, no city-integrated mapping. Commercial platform.

**Unite Us**

- Leading closed-loop referral platform
- HIPAA/HITRUST compliant, EHR integration (Epic, Oracle)
- Secure referral tracking with resolution statuses
- 44+ states, 1.5M+ services
- _Limitations:_ Healthcare-focused. Requires organizational adoption — not a resident-self-service tool. Not a discovery platform.

**Single Stop**

- Benefits screening covering healthcare, food, utilities in 15 minutes
- Regulatory engine incorporating thousands of pages of rules
- Strong university campus deployment model
- _Limitations:_ Not a city-specific platform. No mapping, no AI conversation, no proactive risk assessment.

---

## 2. Gap Analysis: What Nobody Has Done

| Capability                           | ACCESS NYC | LifeSG  | TAMM    | Denver Sunny  | findhelp | Unite Us | **Austin SG**                |
| ------------------------------------ | ---------- | ------- | ------- | ------------- | -------- | -------- | ---------------------------- |
| AI conversational intake             | -          | -       | Yes     | Partial (FAQ) | -        | -        | **Yes**                      |
| Benefits eligibility screening       | Yes (40+)  | Partial | Partial | -             | Yes      | -        | **Yes**                      |
| Proactive risk assessment            | -          | -       | -       | -             | -        | -        | **Yes**                      |
| Life-event pathways                  | -          | Yes     | Yes     | -             | -        | -        | **Yes**                      |
| Interactive service map              | -          | -       | -       | -             | Basic    | -        | **Yes**                      |
| Family/household mode                | Partial    | Partial | -       | -             | -        | -        | **Yes**                      |
| Closed-loop referral tracking        | -          | -       | Partial | -             | Yes      | Yes      | **P2**                       |
| No-account-first design              | Yes        | -       | -       | Yes           | Partial  | -        | **Yes**                      |
| Multilingual (full content)          | 11 langs   | 4 langs | 2 langs | 72 (AI)       | Limited  | Limited  | **100+ (all AI, real-time)** |
| Transit integration                  | -          | -       | -       | -             | -        | -        | **Yes**                      |
| Equity analytics                     | -          | -       | -       | -             | -        | Partial  | **Yes**                      |
| Admin console                        | -          | Yes     | Yes     | -             | Yes      | Yes      | **Yes**                      |
| Open-source / white-label            | Partial    | -       | -       | -             | -        | -        | **Yes**                      |
| City+nonprofit+state+federal unified | -          | -       | Yes     | -             | Yes      | Partial  | **Yes**                      |
| Benefits dollar calculator           | Partial    | -       | -       | -             | Partial  | -        | **Yes**                      |
| Crisis emergency pathway             | -          | -       | -       | -             | -        | -        | **Yes**                      |
| Community reviews/tips               | -          | -       | -       | -             | -        | -        | **P3**                       |

**Key insight:** No existing system combines AI-powered conversational intake + benefits eligibility screening + proactive risk assessment + interactive mapping + life-event pathways + family mode + equity analytics + admin console in a single platform. Austin Service Guide would be the first.

---

## 3. Innovation Features: How Austin Service Guide Leapfrogs the Field

### 3.1 Innovations No One Has Implemented

**1. AI-Powered Risk Prevention Engine**
No existing city portal proactively identifies risk factors and surfaces prevention services. Current systems are reactive — residents must know what they need and search for it. Austin Service Guide flips this: the AI analyzes intake responses to identify risks the resident may not be aware of (housing instability, food insecurity, healthcare gaps) and surfaces prevention services before crisis hits.

_Why this matters:_ The cost of prevention is a fraction of crisis intervention. NYC's predictive homelessness model showed that early intervention can divert families from shelter systems entirely. Austin's Homeless Strategy Office identified a $101M funding gap — prevention is the only way to close it.

**2. Conversational AI Intake (Not a Chatbot)**
Denver Sunny and Granicus GXA are chatbots — they answer questions about city services. Austin Service Guide's AI navigator is fundamentally different: it conducts a structured intake conversation, adapts questions dynamically based on answers, extracts a comprehensive resident profile, and uses that profile for intelligent service matching. This is the difference between a search engine and a personal concierge.

_Why this matters:_ ACCESS NYC's form-based screener gets high usage (no account required, fast) but misses context. A conversational approach captures nuance ("I'm working part-time while caring for my mother who has dementia") that forms can't.

**3. Family/Household Service Mapping**
No existing portal lets a resident do a single intake for their entire household and see services mapped to each family member. A mother with three children, an aging parent, and a veteran spouse currently needs to navigate five separate eligibility paths. Austin Service Guide collapses this into one session.

**4. Equity-Native Architecture**
Civic tech platforms track usage metrics. Austin Service Guide goes further: it compares portal usage demographics against Austin census data in real time, identifies underrepresented populations, and surfaces geographic service deserts. This aligns directly with Austin's Equity Assessment Tool framework and the Office of Equity and Inclusion's mission.

**5. Benefits Dollar Calculator**
Showing a resident that they may be eligible for "$847/month in combined benefits" is fundamentally more motivating than showing a list of program names. Single Stop does basic benefit estimation; Austin Service Guide calculates combined value across all matched programs — SNAP + utility assistance + childcare subsidies + healthcare savings — and presents it as a tangible number.

**6. Crisis Detection with Immediate Intervention**
No existing portal monitors intake responses for crisis indicators and interrupts the flow with emergency resources. Current systems require the resident to navigate to the right page. Austin Service Guide's AI detects crisis language in real time and immediately surfaces 911, 988, SAFE Alliance, Integral Care, and 211 — with click-to-call buttons.

### 3.2 Innovations That Improve on Existing Approaches

**7. Life-Event Pathways (Improved)**
Singapore's LifeSG pioneered life-event organization. Austin Service Guide improves on it by: (a) covering nonprofit and federal programs, not just city services, (b) using AI to personalize within each pathway, and (c) offering the pathway as an entry point that can expand into a full intake.

**8. Interactive Map with Transit (Improved)**
findhelp.org has basic mapping. Austin Service Guide adds: Capital Metro transit routing, color-coded pins by category, real-time "open now" filtering, distance radius filters, and a high-contrast accessible map option. Showing a resident that Clinic A is "22 minutes by bus from your location" is more actionable than showing a pin on a map.

**9. No-Account-First (Improved)**
ACCESS NYC pioneered no-account-required screening. Austin Service Guide preserves this principle and extends it: the full AI intake, service matching, risk assessment, and interactive map all work without an account. Accounts unlock persistence, tracking, and notifications — but are never required.

**10. Multilingual with Transparency (Improved)**
MyLA311 claims 224 languages via AI translation but uses a basic Google Translate widget; ACCESS NYC offers 11 human-translated languages but is limited to static content. Austin Service Guide takes a fundamentally different approach: the AI chat assistant itself is the translation engine. Powered by GPT-5.4-mini on Azure OpenAI, the assistant conducts conversations natively in 100+ languages, detects the resident's language automatically, accepts mid-conversation language switches ("habla español"), and uses tool calls to search the English-canonical service catalog with cross-lingual intent matching — translating queries, retrieving results, and presenting them in the resident's language in real time. This means unlimited language support with zero static translation maintenance. Arabic receives full RTL layout support. Crisis/emergency content is pre-cached in Austin's top 7 non-English languages for instant display.

---

## 4. Competitive Positioning Statement

**Austin Service Guide** is the first open-source, AI-powered resident service platform that unifies city, county, state, federal, and nonprofit services into a single conversational experience — matching residents to every program they're eligible for, identifying risks they may not be aware of, and showing them exactly where and how to access help on an interactive map.

It exceeds every existing system by combining capabilities that have never been brought together: the eligibility screening depth of ACCESS NYC, the life-event design of Singapore's LifeSG, the AI intelligence of Abu Dhabi's TAMM, the accessibility of Denver's Sunny, and the comprehensive directory of findhelp — plus risk prevention, family mode, equity analytics, and transit integration that no platform offers today.

Built on the civic-ai-starter open-source template, it can be deployed by any city, county, or public health organization — making it not just a solution for Austin, but a model for every city in America.

---

## 5. Known Risks & Mitigations from the Field

| Risk                         | Evidence from Other Cities                                                                                                                  | Mitigation                                                                                                                                                                                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AI policy encoding**       | Route Fifty found Denver's Sunny routes homelessness questions to code enforcement — encoding a policy position, not providing neutral help | AI responses grounded in service catalog via RAG; no policy positions; human review of AI conversation templates                                                                                                                                          |
| **Black hole problem**       | Chicago Inspector General found 311 marked requests "completed" when unresolved, fostering distrust                                         | Transparent status tracking; no auto-closure; resident confirmation of resolution                                                                                                                                                                         |
| **Status dishonesty**        | NYC 311 report cards gave multiple agencies "F" grades; 20% of rodent complaints "resolved" before they were submitted                      | Honest status language; "in progress" means in progress; audit log for status changes                                                                                                                                                                     |
| **AI hallucination**         | General LLM risk — chatbots inventing services that don't exist                                                                             | RAG-only architecture; AI never invents services; all recommendations cite specific catalog entries                                                                                                                                                       |
| **Digital divide exclusion** | 8% of Austin adults don't use internet; non-users concentrated in Southwest Austin                                                          | Multi-channel access (web, mobile, kiosk, SMS); library/community center partnerships; no-account-required design                                                                                                                                         |
| **Data privacy erosion**     | Long Beach research found residents hesitant about data sharing due to unclear access policies                                              | Data minimization; no PII stored for anonymous sessions; plain-language privacy notices; resident data deletion                                                                                                                                           |
| **Stale service data**       | Universal problem — service catalogs become outdated                                                                                        | Verification workflow with configurable re-check intervals; last-verified dates displayed; community-flagging of outdated info                                                                                                                            |
| **Translation quality**      | Machine translation can mislead on eligibility criteria                                                                                     | GPT-5.4-mini provides high-quality contextual translation (not word-for-word); AI system prompt enforces culturally appropriate tone; crisis content pre-cached for instant delivery; service catalog is English-canonical with AI translation at runtime |

---

## 6. Sources

### City Portals

- ACCESS NYC: access.nyc.gov
- MyLA311: myla311.lacity.gov
- CHI311: 311.chicago.gov
- BOS:311: boston.gov/departments/boston-311
- Austin 311: 311.austintexas.gov
- SF.gov: sf.gov
- LifeSG: life.gov.sg
- TAMM 3.0: tamm.abudhabi
- e-Estonia: e-estonia.com

### Benefits Platforms

- findhelp: findhelp.org
- Unite Us: uniteus.com
- Single Stop: singlestop.org
- One Degree: 1degree.org
- Benefits.gov / USA.gov: usa.gov/benefit-finder

### AI Civic Tech

- Granicus GXA: granicus.com/gxa
- Citibot / Denver Sunny: citibot.io
- Texas by Texas (TxT): txt.texas.gov

### Research & Analysis

- Chicago OIG 311 Audit, February 2026
- Route Fifty: "I Tested 3 City AI Chatbots," March 2026
- NYC 311 Report Cards, Local Law 13 of 2025
- Deloitte Government Trends 2026 — Agentic AI for Government
- Center for Civic Futures: $8.5M AI grants for public benefits
- Microsoft: "Right Benefit, Right Person, Right Time," March 2026
- DOJ Web Accessibility Rule: WCAG 2.1 AA by April 2026
- 2025 Austin-Travis County Community Health Assessment
- Austin Digital Inclusion Trailblazer Award, 2025
- Bloomberg City Data Alliance selection
