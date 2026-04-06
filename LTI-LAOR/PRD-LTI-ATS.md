# LTI ATS — Product Requirements Document

**Version:** 1.0  
**Author:** Luis Ovando (LAOR)  
**Date:** 2026-04-05  
**Status:** Draft

---

## 1. Executive Summary

We're building **LTI ATS**, an AI-native Applicant Tracking System for HR teams and talent acquisition professionals at tech startups and scale-ups (10–1,000 employees), to solve the problem of slow, fragmented, and expensive hiring workflows dominated by legacy tools with opaque pricing and bolt-on AI. LTI ATS embeds artificial intelligence into every pipeline stage — job description drafting, semantic CV matching, automated screening, and interview summarization — and delivers a real-time collaborative workspace with transparent freemium pricing and self-service onboarding in under one week. The expected impact is a 40% reduction in time-to-fill and a 3× improvement in recruiter operational efficiency within 90 days of adoption.

---

## 2. Problem Statement

### Who has this problem?
Recruiters and Hiring Managers at tech startups (10–200 employees) and growing scale-ups (200–1,000 employees), as well as staffing agencies, who currently manage hiring through a combination of spreadsheets, email threads, and expensive legacy ATS platforms.

### What is the problem?
Current ATS solutions force HR teams to choose between:
- **Expensive and slow:** Greenhouse ($6,500–$70,000+/year, 4–8 week implementation), Lever ($12,000+/year, 2–4 weeks setup)
- **Affordable but limited:** Workable ($169–$599/month, AI only as an expensive add-on)

In all cases:
1. **AI is cosmetic, not functional** — limited to keyword matching; does not assist with job description writing, candidate scoring, interview summarization, or bias detection
2. **Collaboration is asynchronous and fragmented** — hiring managers give feedback via email/Slack, outside the ATS, breaking traceability
3. **Onboarding takes weeks** — implementation consultants, training programs, and professional services create barriers for small teams
4. **Pricing is opaque** — no self-service; enterprise sales-gated; no functional free tier

### Why is it painful?
- **Recruiter impact:** Spends 30–40% of time on administrative tasks (copy-pasting data between tools, chasing interview feedback, updating spreadsheet pipelines)
- **Business impact:** Average time-to-fill of 40–60 days in tech; each day of vacancy costs ~$500–$1,500 in lost productivity
- **Candidate impact:** Slow, impersonal processes lead to offer drop-offs; 60% of candidates abandon applications that take more than 15 minutes

### Evidence (from project brief and market context)
- Greenhouse charges $1,000–$15,000 in implementation fees *on top* of license — barrier for small teams
- Workable's AI sourcing is listed as basic; online assessments require a $59/month add-on
- Lever's AI Interview Companion is an add-on, not included in base plan
- Exit surveys across ATS users consistently cite "didn't know what to do first" (onboarding friction) and "feedback got lost" (collaboration gaps) as top churn drivers

---

## 3. Target Users & Personas

### Primary Persona: Rachel — The Recruiter at a Series A Startup

- **Role:** HR Generalist / Recruiter (wears many hats)
- **Company size:** 30–150 employees
- **Tech savviness:** Medium-high (uses Slack, Notion, Google Workspace daily)
- **Goals:** Fill 5–15 open roles per quarter with quality candidates, fast
- **Pain points:**
  - Spends too much time on manual CV screening and scheduling logistics
  - Loses candidate context when feedback lives in Slack and email
  - Can't easily justify hiring decisions to the CEO without data
  - Gets pushback from hiring managers who "don't have time" for ATS tools
- **Current behavior:** Uses a combination of LinkedIn Recruiter, a basic ATS, and Google Sheets for tracking
- **Jobs-to-be-done:** "Help me move the right candidates through faster, without chasing people for feedback."

### Secondary Persona: Marcus — The Hiring Manager

- **Role:** Engineering Manager or Head of Product
- **Company size:** 50–500 employees
- **Tech savviness:** Medium (lives in Jira/Linear, not HR tools)
- **Goals:** Hire strong team members without disrupting engineering work
- **Pain points:**
  - ATS tools are not designed for his workflow; too many steps to leave feedback
  - Doesn't want to log into a separate system; prefers notifications + quick actions
  - Frustrated when candidates he liked get lost in the pipeline without a decision
- **Jobs-to-be-done:** "Let me evaluate and give my opinion on candidates quickly, without leaving my flow."

### Tertiary Persona: Ana — The HR Admin at a Mid-Market Company

- **Role:** HR Director / People Ops Lead
- **Company size:** 200–1,000 employees
- **Goals:** Standardize hiring across multiple departments, ensure compliance and DEI goals
- **Pain points:**
  - Lacks consolidated analytics across departments and roles
  - Pipeline processes differ by team with no consistency
  - No single source of truth for audit trails or compliance
- **Jobs-to-be-done:** "Give me a platform that standardizes hiring and shows me where we're losing candidates."

---

## 4. Strategic Context

### Business Goals

| Goal | Link to LTI ATS |
|---|---|
| **Reduce time-to-fill** | Automate screening, scheduling, and handoffs to eliminate wait time |
| **Increase operational efficiency** | AI assistance + automation removes manual tasks for recruiters |
| **Improve collaboration quality** | Real-time workspace for recruiters, HMs, and interviewers |
| **Drive PLG growth** | Freemium tier enables self-service adoption with zero sales friction |
| **Build a data moat** | Each hiring process trains the AI matching model, improving over time |

### Market Opportunity

- **TAM:** $3.8B global ATS market (2025), projected $6.5B by 2030
- **SAM:** ~$1.2B — tech startups and scale-ups globally (10–1,000 employees using SaaS HR tools)
- **SOM (Year 2):** ~$30M ARR — 5,000 paying teams at avg $500/month via PLG + inside sales motion

### Competitive Landscape

| Dimension | Greenhouse | Lever | Workable | **LTI ATS** |
|---|---|---|---|---|
| **Pricing** | Opaque, from $6,500/yr | Opaque, from $12,000/yr | $169–$599/mo + extras | Transparent, freemium + clear tiers |
| **Integrated AI** | Expert plan only | AI add-on | Basic AI sourcing | Native AI at every stage |
| **Onboarding** | 4–8 weeks | 2–4 weeks | 1–2 weeks | < 1 week (self-service) |
| **Collaboration** | Scorecards + feedback | Shared pipeline | Notes + evaluations | Real-time with presence and notifications |

### Why Now?

1. **LLM costs dropped 80%+ in 2024–2025** — AI features that were cost-prohibitive are now viable at startup scale
2. **PLG motion proven in adjacent markets** (Notion, Linear, Figma) — self-serve SaaS in HR is underexplored
3. **Post-2023 hiring wave** — tech companies are rebuilding TA capacity after layoffs; new teams are evaluating tools fresh
4. **Regulatory push for DEI and audit trails** — compliance requirements create urgency for structured, trackable hiring processes

---

## 5. Solution Overview

LTI ATS is a cloud-native, AI-embedded Applicant Tracking System delivered as a SaaS web application. It replaces the spreadsheet + email + basic ATS patchwork with a single collaborative workspace designed around reducing time-to-fill and improving candidate experience.

### Core Workflow

```text
Job Creation (AI-assisted) → Multichannel Publishing → Automated Candidate Intake →
AI Screening + Filters → Collaborative Evaluation (Tests + Interviews + Scorecards) →
Offer Generation (e-sign) → Hiring → HRIS Handoff
```

### Key Capabilities

**1. AI-Assisted Job Creation**  
The recruiter provides a job title and seniority level; the AI generates a complete, inclusive, conversion-optimized job description. The recruiter reviews and publishes.

**2. Multichannel Publishing**  
One-click simultaneous publishing to LinkedIn, Indeed, Glassdoor, the company's career site (embeddable widget), and internal referral program. Source-of-hire is tracked per channel.

**3. Smart Candidate Intake**  
Automatic CV parsing extracts structured data (skills, experience, education, contact). AI generates a semantic match score (0–100) per candidate-job pair with human-readable explanation. Knockout questions auto-filter unqualified applicants.

**4. Visual Pipeline (Kanban)**  
Each job has a configurable Kanban pipeline (applied → screening → test → interview → offer → hired). Candidates move through stages with full activity timeline and audit trail.

**5. Native Assessments**  
Create technical, coding, or psychometric tests from a question bank or via AI generation. Candidates take tests in-platform; scoring is automatic with configurable thresholds.

**6. Smart Scheduling**  
Calendar integration (Google Calendar, Outlook) with auto-scheduling based on panel availability. Candidates self-schedule via a public link with configurable time slots.

**7. Structured Scorecards + Decision Panel**  
Each interviewer completes a competency-based scorecard. The decision panel consolidates all scores, notes, and recommendations in one view for the Hiring Manager.

**8. Offer Management**  
Generate offer letters from configurable templates with salary, benefits, and start date. Candidates receive and sign electronically. System tracks acceptance/rejection/expiry.

**9. Analytics Dashboards**  
Real-time dashboards for time-to-hire, source effectiveness, pipeline conversion by stage, and DEI metrics. Proactive alerts when a stage has bottlenecks (e.g., candidates idle > 5 days).

### Architecture Overview

Event-driven microservices on Kubernetes (AWS/GCP), PostgreSQL per service with Row-Level Security for multi-tenancy, Kafka event bus, Redis cache, S3 for files, Elasticsearch for full-text search, pgvector for semantic embeddings. React SPA + candidate portal + embeddable widget as clients.

---

## 6. Success Metrics

### Primary Metric
**Time-to-fill** (calendar days from job published to offer accepted)
- **Current benchmark (industry avg):** 40–60 days
- **Target at 90-day mark (for active users):** ≤ 28 days
- **Measurement:** Median across all closed jobs by paying teams in their first 90 days

### Secondary Metrics

| Metric | Current Baseline | Target |
|---|---|---|
| Recruiter setup time (first job live) | 1–2 weeks (competitors) | < 60 minutes |
| CV screening time per application | ~8 minutes manual | < 2 minutes with AI assist |
| Interview feedback collection rate | ~40% within 24h (email-based) | ≥ 80% within 24h |
| PLG activation rate (free → first job published) | — | ≥ 60% within 7 days of signup |
| Free-to-paid conversion | — | ≥ 15% within 60 days |
| Monthly churn (paid teams) | — | < 3% |

### Guardrail Metrics
- **Candidate NPS:** Must not fall below 40 (slow or impersonal processes damage employer brand)
- **Data accuracy of AI parsing:** CV structured data must be ≥ 95% accurate (measured by recruiter correction rate)
- **System availability:** ≥ 99.9% uptime for core pipeline features

---

## 7. User Stories & Requirements

### Epic Hypothesis

> We believe that providing a unified AI-native ATS with real-time collaboration for recruiters and hiring managers at tech startups will reduce time-to-fill by 40% and achieve 15% free-to-paid conversion within 60 days, because current solutions force fragmented workflows, charge opaque prices, and offer no useful AI. We'll validate this with median time-to-fill and activation metrics 90 days after launch.

---

### Epic 1: Job Posting & Multichannel Publishing

**US-01 — AI-Assisted Job Description**  
*As a Recruiter, I want to generate a job description draft using AI so that I can save time while creating high-quality, inclusive postings.*

**Acceptance Criteria:**
- [ ] Given a job title and seniority level, the AI generates a full description (summary, responsibilities, requirements, benefits) in < 10 seconds
- [ ] The generated description includes inclusive language guidelines (no gendered words)
- [ ] The recruiter can edit any section inline before saving
- [ ] The description can be saved as a reusable template

---

**US-02 — Configure Knockout Questions**  
*As a Recruiter, I want to set knockout questions for a job posting so that unqualified candidates are automatically filtered before manual review.*

**Acceptance Criteria:**
- [ ] Recruiter can add 1–10 knockout questions per job
- [ ] Each question supports: yes/no, multiple choice, or numeric comparison
- [ ] Recruiter marks which answer(s) disqualify the candidate
- [ ] Candidates who fail knockout questions are auto-rejected and optionally notified
- [ ] Pipeline shows count of auto-rejected vs. passed candidates

---

**US-03 — Multichannel Publication**  
*As a Recruiter, I want to publish a job simultaneously to multiple channels so that I reach more candidates without manual repetition.*

**Acceptance Criteria:**
- [ ] Recruiter can select one or more channels: LinkedIn, Indeed, Glassdoor, company career site, internal referral
- [ ] Publish action distributes to all selected channels in one click
- [ ] Each application records the source channel (for analytics)
- [ ] Recruiter can pause or expire a publication per channel independently

---

### Epic 2: Candidate Intake & AI Screening

**US-05 — Automatic CV Parsing**  
*As a Recruiter, I want CVs to be automatically parsed into structured profiles so that I don't spend time manually extracting data.*

**Acceptance Criteria:**
- [ ] When a candidate submits a CV (PDF or DOCX), the system extracts: name, email, phone, work experience (company, role, dates), education, skills, and LinkedIn URL
- [ ] Parsed data is displayed on the candidate profile card within 30 seconds of submission
- [ ] Recruiter can manually override any extracted field
- [ ] System flags low-confidence parsed fields for manual review

---

**US-06 — AI Semantic Match Score**  
*As a Recruiter, I want each application to show an AI-generated match score so that I can prioritize candidates with the best fit.*

**Acceptance Criteria:**
- [ ] Each application shows a score from 0–100 based on semantic similarity between candidate profile and job requirements
- [ ] Score includes a short explanation (top 3 matching strengths and top 1–2 gaps)
- [ ] Recruiter can sort and filter the pipeline by match score
- [ ] Score is recalculated if the recruiter updates the job requirements

---

**US-07 — Duplicate & Blacklist Detection**  
*As a Recruiter, I want the system to detect duplicate applications and blacklisted candidates so that I don't process invalid applications.*

**Acceptance Criteria:**
- [ ] System detects duplicate applications (same email + same job) and merges or flags them
- [ ] System checks against company-level blacklist on application receipt
- [ ] Blacklisted candidates are auto-rejected with an internal note (not visible to candidate)
- [ ] Recruiter can add/remove candidates from the blacklist from their profile

---

### Epic 3: Collaborative Evaluation

**US-09 — Send Online Assessment**  
*As a Recruiter, I want to send an online test to a candidate so that I can evaluate technical skills before scheduling interviews.*

**Acceptance Criteria:**
- [ ] Recruiter can create or select an existing assessment (technical, psychometric, or coding)
- [ ] Assessment can be generated with AI from a topic/skill description
- [ ] Candidate receives email with test link and deadline
- [ ] Test has a configurable time limit; auto-submits on timeout
- [ ] Results are automatically scored and added to the candidate's pipeline card
- [ ] Recruiter sees pass/fail based on configurable threshold

---

**US-10 — Smart Interview Scheduling**  
*As a Recruiter, I want to schedule interviews using calendar availability so that I can avoid back-and-forth coordination.*

**Acceptance Criteria:**
- [ ] Recruiter selects interviewers and the system reads their calendar availability (Google/Outlook)
- [ ] System suggests available time slots based on all panelists' free time
- [ ] Candidate receives a self-scheduling link with available slots
- [ ] Confirmed interview appears in all participants' calendars with video link (Google Meet / Zoom)
- [ ] Automatic reminder sent to all parties 24h before the interview

---

**US-11 — Competency-Based Scorecard Submission**  
*As an Interviewer, I want to complete a structured scorecard after each interview so that my feedback is captured consistently and on time.*

**Acceptance Criteria:**
- [ ] Scorecard template is configurable per job or pipeline stage
- [ ] Each scorecard includes: competency ratings (1–5 scale), written notes, and an overall recommendation (Strong Yes / Yes / Neutral / No / Strong No)
- [ ] Interviewer receives an in-app and email notification to complete scorecard within 24h
- [ ] Recruiter can see which interviewers have not yet submitted feedback
- [ ] Scorecard is locked after Hiring Manager makes a final decision

---

**US-12 — Decision Panel Review**  
*As a Hiring Manager, I want to see a consolidated panel of all interviewer feedback so that I can make a final hiring decision quickly and confidently.*

**Acceptance Criteria:**
- [ ] Decision panel shows all scorecards for a candidate, side by side, per interview stage
- [ ] Overall scores and recommendation distribution (count of Yes / No votes) are summarized at the top
- [ ] Hiring Manager can leave a final decision note and mark the candidate as Advance / Reject
- [ ] Decision is recorded in the application timeline with timestamp and actor

---

### Epic 4: Offer & Hiring

**US-14 — Offer Letter Generation & E-Signature**  
*As a Recruiter, I want to generate an offer letter from a template so that I can extend offers quickly and consistently.*

**Acceptance Criteria:**
- [ ] Recruiter selects an offer template and fills in: salary, currency, benefits, start date
- [ ] System generates a formatted offer document (PDF)
- [ ] Offer is sent to the candidate via email with an e-signature request
- [ ] Recruiter can track offer status: draft → sent → accepted / rejected / expired
- [ ] System sends automatic reminder to candidate if offer is not signed within 3 days

---

**US-15 — Candidate Rejection & Talent Pool Archiving**  
*As a Recruiter, I want rejected candidates to be optionally added to a talent pool so that I can consider them for future openings.*

**Acceptance Criteria:**
- [ ] When a candidate is rejected, recruiter can choose to add them to the talent pool with tags (e.g., "senior backend", "future lead")
- [ ] Candidate receives a rejection notification; content is configurable per company
- [ ] Talent pool is searchable and filterable by tag, skills, and application history
- [ ] Talent pool candidates can be directly added to a new job's pipeline without reapplying

---

### Epic 5: Analytics & Reporting

**US-17 — Time-to-Hire Dashboard**  
*As an HR Director, I want to see a real-time time-to-hire dashboard so that I can identify bottlenecks and optimize the hiring process.*

**Acceptance Criteria:**
- [ ] Dashboard shows: average and median time-to-fill per job, per department, and company-wide
- [ ] Stage conversion rates show drop-off percentage at each pipeline stage
- [ ] Source effectiveness report shows candidate volume and hired rate per channel
- [ ] Bottleneck alerts trigger when candidates are idle in a stage for > 5 configurable days
- [ ] Data refreshes in real time (or within 1 hour max)

---

## 8. Out of Scope (MVP)

The following are explicitly excluded from the first release:

| Feature | Rationale |
|---|---|
| Mobile native app (iOS/Android) | Desktop-first; validate web experience before investing in mobile |
| Video interviewing built-in | High build cost; integrate with Zoom/Google Meet via link instead |
| HRIS write-back (automated sync) | API integration requires per-HRIS custom work; manual export as CSV first |
| Advanced DEI bias detection | AI bias detection requires a dedicated ML pipeline; include basic flags only |
| Multi-language interface | English-first for initial target market (US/UK/LatAm tech) |
| Custom domain for candidate portal | Infrastructure complexity; use subdomain (company.lti.io) first |
| Gamification / points system for assessments | Nice-to-have; validate core assessment flow first |
| Background check integrations | Compliance-heavy; partner integrations in roadmap Phase 2 |

---

## 9. Dependencies & Risks

### Technical Dependencies

| Dependency | Owner | ETA | Risk |
|---|---|---|---|
| OpenAI API (or equivalent LLM) for AI features | External | Available now | Cost per API call must stay within unit economics ($0.02–0.05/application) |
| Google Calendar API + Outlook OAuth | External | Available now | OAuth scopes approval can delay |
| LinkedIn Job Posting API | External | 2–4 week approval | LinkedIn API access requires partner program enrollment |
| pgvector extension (PostgreSQL) | Infrastructure | Sprint 1 | Needs Postgres 15+ and GPU-enabled instance for embedding generation |
| e-Signature provider (DocuSign or HelloSign) | External | Available now | Integration + legal review needed |

### Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| AI match scores are perceived as inaccurate or biased | Medium | High | Show explainability notes with every score; allow recruiter to override; monitor correction rate |
| LinkedIn API access delayed | High | Medium | Launch without LinkedIn integration; add manual "copy link" flow as fallback |
| Calendar integration breaks for Outlook users | Medium | High | Support manual scheduling as fallback; prioritize Google Calendar first |
| Free tier abuse (high-volume low-intent signups) | Medium | Low | Limit free tier to 2 active jobs + 1 user; add email verification on signup |
| LLM API costs spike at scale | Low | High | Cache CV parsing results; set per-company monthly AI token budgets |

---

## 10. Open Questions

| # | Question | Owner | Target Decision Date |
|---|---|---|---|
| 1 | Should the free tier include AI match scoring, or only on paid plans? | PM | 2026-04-15 |
| 2 | Which e-signature provider to integrate first: DocuSign vs. HelloSign vs. native? | Engineering | 2026-04-20 |
| 3 | Should the Candidate Portal have its own domain or be a subdomain of the client's site? | Design + PM | 2026-04-15 |
| 4 | Do we build AI assessment generation in MVP or use a question bank only? | PM + Engineering | 2026-04-10 |
| 5 | What is the data retention policy for rejected candidate CVs (GDPR compliance)? | Legal + PM | 2026-04-30 |
| 6 | Should interviewers be able to see each other's scorecards before submitting their own? | PM + UX | 2026-04-20 |
