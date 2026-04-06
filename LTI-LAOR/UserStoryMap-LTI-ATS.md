# LTI ATS — User Story Map

**Framework:** Jeff Patton's Story Mapping  
**Author:** Luis Ovando (LAOR)  
**Date:** 2026-04-05  
**Based on:** PRD-LTI-ATS.md  

---

## Context

### Segment
Tech startups and scale-ups (10–1,000 employees) running active hiring pipelines — specifically TA teams using a patchwork of spreadsheets, email, and basic ATS tools.

### Primary Persona: Rachel — Recruiter at a Series A Startup
35, HR Generalist who owns the full hiring lifecycle. Uses Slack, Notion, and Google Workspace daily. Manages 5–15 open roles per quarter. Frustrated by manual CV screening, chasing feedback from hiring managers over email, and ATS tools that don't fit her workflow. Wants to move the right candidates through faster without losing context.

### Narrative
> Rachel needs to take a new role from requisition to hired — sourcing, screening, evaluating, and closing the right candidate — as fast as possible, with full traceability and zero chasing.

---

## Story Map — Overview (Backbone)

```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 ACTIVITY 1          ACTIVITY 2          ACTIVITY 3          ACTIVITY 4
 Create & Configure  Publish & Attract   Screen & Filter     Evaluate Candidates
 the Job Opening     Candidates          Applicants          (Tests + Interviews)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 ACTIVITY 5          ACTIVITY 6
 Select & Make       Close Process
 the Offer           & Learn
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Full Story Map (Activities → Steps → Tasks)

---

### ACTIVITY 1 — Create & Configure the Job Opening

*Rachel receives a hire request from the Hiring Manager and prepares the job opening in LTI ATS.*

---

#### Step 1.1 — Define the role and write the job description

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Enter job title, department, location, employment type, and salary range | US-01 |
| 🟢 MVP | Request AI to generate a job description draft based on title + seniority | US-01 |
| 🟢 MVP | Review and edit the AI-generated description inline | US-01 |
| 🟡 R2 | Mark description language as inclusive (AI flags gendered/exclusionary words) | US-01 |
| 🟡 R2 | Save the finalized description as a reusable template | US-01 |
| 🔵 R3 | Assign a hiring manager to the role from the user directory | — |
| 🔵 R3 | Set headcount (number of hires) for the same role | — |

---

#### Step 1.2 — Configure the hiring pipeline

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Select or create a pipeline template for the role (e.g., "Engineering Hiring") | — |
| 🟢 MVP | View and reorder pipeline stages (applied → screening → test → interview → offer → hired) | — |
| 🟡 R2 | Add a custom stage to the pipeline (e.g., "Portfolio Review") | — |
| 🟡 R2 | Configure auto-advance rules per stage (e.g., auto-advance if test score ≥ 80%) | — |
| 🔵 R3 | Clone pipeline configuration from a previous job opening | — |

---

#### Step 1.3 — Set automated screening filters

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Add knockout questions to the application form (yes/no, multiple choice, numeric) | US-02 |
| 🟢 MVP | Mark disqualifying answer(s) for each knockout question | US-02 |
| 🟢 MVP | Preview the candidate-facing application form | US-02 |
| 🟡 R2 | Add optional screening questions (not knockout, but informational) | — |
| 🟡 R2 | Set minimum required skills from a standard taxonomy | — |
| 🔵 R3 | Configure AI-minimum match score threshold for auto-advancement | US-06 |

---

### ACTIVITY 2 — Publish & Attract Candidates

*Rachel publishes the job opening to reach the widest qualified candidate pool across all channels.*

---

#### Step 2.1 — Select and configure publishing channels

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Select publishing channels: company career site, LinkedIn, Indeed, Glassdoor, referral | US-03 |
| 🟢 MVP | Set expiration date per channel | US-03 |
| 🟡 R2 | Preview how the job listing will appear on each channel | US-03 |
| 🟡 R2 | Configure internal referral incentive message | US-03 |
| 🔵 R3 | Schedule auto-repost if job is still open after N days | — |

---

#### Step 2.2 — Publish the job and track distribution

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Click "Publish" to distribute to all selected channels simultaneously | US-03 |
| 🟢 MVP | See status of each publication (active / pending / failed) | US-03 |
| 🟡 R2 | Pause or expire a publication on a specific channel without closing the job | US-03 |
| 🟡 R2 | Copy shareable job link for manual distribution (LinkedIn post, WhatsApp, etc.) | — |
| 🔵 R3 | A/B test two job description variants to compare application conversion | — |

---

#### Step 2.3 — Manage the candidate application portal

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Candidate submits application via career site or job board apply link | US-05 |
| 🟢 MVP | Candidate uploads CV (PDF / DOCX) and answers knockout questions | US-02, US-05 |
| 🟡 R2 | Candidate can track application status in a public-facing portal | — |
| 🔵 R3 | Candidate receives auto-confirmation email upon submission | — |
| 🔵 R3 | Embed career site widget on company website (no redirect needed) | — |

---

### ACTIVITY 3 — Screen & Filter Applicants

*Rachel reviews the incoming candidate pool and identifies who advances to evaluation.*

---

#### Step 3.1 — Process automatic intake and AI scoring

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | System parses submitted CV and populates structured candidate profile | US-05 |
| 🟢 MVP | System applies knockout question logic and auto-rejects disqualified candidates | US-02 |
| 🟢 MVP | System checks for duplicates and blacklisted candidates; flags or auto-rejects | US-07 |
| 🟢 MVP | System calculates AI semantic match score (0–100) per candidate-job pair | US-06 |
| 🟡 R2 | System generates short score explanation (top 3 strengths, top 2 gaps) | US-06 |
| 🟡 R2 | Flag low-confidence parsed fields for manual recruiter review | US-05 |

---

#### Step 3.2 — Review and triage the pipeline

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | View the Kanban pipeline for a job opening with all candidates per stage | — |
| 🟢 MVP | Sort and filter candidates by match score, application date, or source channel | US-06 |
| 🟢 MVP | Open a candidate profile card (parsed CV, scores, knockout answers, timeline) | US-08 |
| 🟡 R2 | Add an internal note to a candidate's profile (visible to team, not to candidate) | — |
| 🟡 R2 | Tag a candidate (e.g., "strong technical", "culture risk") | — |
| 🔵 R3 | Bulk-advance or bulk-reject a set of selected candidates | — |

---

#### Step 3.3 — Move candidates and send early communications

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Drag candidate card to next stage (e.g., Screening → Test) | — |
| 🟢 MVP | Reject a candidate and optionally add to talent pool with tags | US-15 |
| 🟢 MVP | System sends rejection email to candidate (configurable template) | US-15 |
| 🟡 R2 | Send a personalized message to a candidate from within the platform | — |
| 🔵 R3 | Search talent pool for previously rejected candidates by skill/tag | US-15 |

---

### ACTIVITY 4 — Evaluate Candidates (Tests + Interviews)

*Rachel, the Hiring Manager, and interviewers collaboratively evaluate shortlisted candidates through tests, interviews, and scorecards.*

---

#### Step 4.1 — Send and track online assessments

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Select or create an assessment for the role (technical, psychometric, coding) | US-09 |
| 🟢 MVP | Send assessment link to one or multiple candidates with a deadline | US-09 |
| 🟢 MVP | Candidate completes test in-platform; system auto-scores and marks pass/fail | US-09 |
| 🟢 MVP | Recruiter sees test result on candidate card and moves to next stage or rejects | US-09 |
| 🟡 R2 | Generate assessment questions with AI from a topic/skill description | US-09 |
| 🟡 R2 | Configure test time limit; auto-submit on timeout | US-09 |
| 🔵 R3 | Build a reusable question bank per department or role family | US-09 |

---

#### Step 4.2 — Schedule interviews

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Select interviewers for the interview panel | US-10 |
| 🟢 MVP | System reads calendar availability of all selected interviewers | US-10 |
| 🟢 MVP | Recruiter selects a time slot from system-suggested available windows | US-10 |
| 🟢 MVP | Candidate receives self-scheduling link and confirms a time slot | US-10 |
| 🟢 MVP | Calendar invite with video link (Google Meet / Zoom) is sent to all participants | US-10 |
| 🟡 R2 | System sends 24h reminder to all participants | US-10 |
| 🟡 R2 | Recruiter reschedules interview from the platform (updates calendar) | — |
| 🔵 R3 | System proposes multi-stage interview sequence (e.g., 3 rounds in one week) | — |

---

#### Step 4.3 — Conduct interview and complete scorecard

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Interviewer receives in-app and email prompt to complete scorecard after interview | US-11 |
| 🟢 MVP | Interviewer fills in competency ratings (1–5) and written notes per criterion | US-11 |
| 🟢 MVP | Interviewer submits overall recommendation (Strong Yes / Yes / Neutral / No / Strong No) | US-11 |
| 🟡 R2 | Recruiter can see which interviewers have not yet submitted feedback | US-11 |
| 🟡 R2 | System generates AI-assisted interview summary from notes or transcript | — |
| 🟡 R2 | Scorecard template is configurable per job or pipeline stage | US-11 |
| 🔵 R3 | Interviewer adds private note visible only to themselves before panel consolidation | — |

---

#### Step 4.4 — Review consolidated decision panel (Hiring Manager)

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Hiring Manager views side-by-side scorecards from all interviewers | US-12 |
| 🟢 MVP | Summary shows recommendation distribution (count of Yes/No votes) and avg scores | US-12 |
| 🟢 MVP | Hiring Manager marks candidate as Advance or Reject with a decision note | US-12 |
| 🟡 R2 | Hiring Manager compares two finalist candidates side by side | — |
| 🔵 R3 | Decision and reasoning are recorded in the candidate timeline with timestamp | US-12 |

---

### ACTIVITY 5 — Select & Make the Offer

*Rachel extends the job offer to the selected candidate and tracks acceptance through e-signature.*

---

#### Step 5.1 — Generate and send the offer

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Recruiter selects an offer template for the role | US-14 |
| 🟢 MVP | Recruiter fills in salary, currency, benefits, and start date | US-14 |
| 🟢 MVP | System generates a formatted PDF offer letter | US-14 |
| 🟢 MVP | System sends offer via email with an e-signature request | US-14 |
| 🟡 R2 | Recruiter previews the offer document before sending | US-14 |
| 🟡 R2 | System sends automatic reminder to candidate if not signed within 3 days | US-14 |
| 🔵 R3 | Offer templates are configurable per role family or department | US-14 |

---

#### Step 5.2 — Track offer response

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | Recruiter tracks offer status: draft → sent → accepted / rejected / expired | US-14 |
| 🟢 MVP | Candidate signs offer electronically; system records signature date | US-14 |
| 🟡 R2 | If candidate rejects, recruiter can reopen process or select next finalist | US-15 |
| 🟡 R2 | System notifies recruiter instantly when offer is signed or rejected | — |
| 🔵 R3 | Offer data (salary, start date) is pre-populated for HRIS export | — |

---

#### Step 5.3 — Close the job and notify remaining candidates

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | System marks the job as "Hired" and closes all active publications | — |
| 🟢 MVP | Remaining pipeline candidates receive rejection notifications (configurable template) | US-15 |
| 🟡 R2 | Recruiter adds strong runners-up to talent pool with tags | US-15 |
| 🔵 R3 | System triggers HRIS data handoff (candidate profile + start date) | — |

---

### ACTIVITY 6 — Close Process & Learn

*Rachel and Ana review hiring outcomes to improve future cycles.*

---

#### Step 6.1 — Review time-to-hire and pipeline analytics

| Priority | Task | User Story Ref |
|---|---|---|
| 🟢 MVP | View dashboard: time-to-fill per job, per department, company-wide | US-17 |
| 🟢 MVP | View stage conversion rates (drop-off % at each pipeline stage) | US-17 |
| 🟡 R2 | View source effectiveness: candidate volume and hired rate per channel | US-18 |
| 🟡 R2 | View bottleneck alerts: stages with candidates idle > configurable threshold | US-17 |
| 🔵 R3 | Export hiring report as PDF or CSV for leadership review | — |
| 🔵 R3 | View DEI metrics: demographic breakdown at each pipeline stage | — |

---

#### Step 6.2 — Improve the process for next time

| Priority | Task | User Story Ref |
|---|---|---|
| 🟡 R2 | Update job template based on what worked (description, filters, pipeline) | US-01 |
| 🟡 R2 | Update scorecard template based on interviewer feedback quality | US-11 |
| 🔵 R3 | Review AI match score accuracy (how many top-scored candidates were hired?) | US-06 |
| 🔵 R3 | Configure proactive bottleneck alert thresholds per stage | US-17 |

---

## Release Slices (Vertical Prioritization)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 🟢 RELEASE 1 — MVP (Months 1–3): Core hiring loop end-to-end
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 Create job → AI description → Knockout filters
 → Publish (career site + manual link)
 → CV auto-parse + AI match score + auto-reject
 → Kanban pipeline view + candidate cards
 → Send assessment + auto-scoring
 → Schedule interview (Google Calendar) + self-scheduling link
 → Scorecard submission
 → Decision panel (HM view)
 → Offer generation + e-signature
 → Close job + reject notifications + talent pool
 → Basic time-to-hire dashboard

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 🟡 RELEASE 2 (Months 4–6): Collaboration depth + channel breadth
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 Inclusive language AI check on job descriptions
 → Template library (role-based)
 → Custom pipeline stages + auto-advance rules
 → Multi-channel publishing (LinkedIn, Indeed, Glassdoor)
 → AI-generated assessments from skill topic
 → AI interview summary from notes
 → Configurable scorecard templates per stage
 → 24h feedback reminders + pending scorecard view
 → Side-by-side finalist comparison
 → Source effectiveness analytics + bottleneck alerts
 → Offer reminder emails + rejection flow with talent pool

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 🔵 RELEASE 3 (Months 7–12): Scale + intelligence + integrations
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 Headcount planning (multiple hires per role)
 → Clone pipeline from previous job
 → AI match score threshold auto-advance
 → Bulk advance / bulk reject actions
 → Talent pool semantic search by skill/tag
 → Multi-stage interview sequence scheduling
 → Scorecard private notes (pre-panel)
 → HRIS data handoff (Workday, BambooHR)
 → DEI metrics dashboard
 → Career site embeddable widget
 → A/B test job description variants
 → Reusable question bank per department
 → Export reports (PDF/CSV) for leadership
```

---

## Gap Analysis & Opportunities

| Gap / Opportunity | Area | Suggested Action |
|---|---|---|
| Hiring Manager has no lightweight "quick vote" without full scorecard | Evaluation | Add a mobile-friendly 5-second rating card (thumbs up/down) as a complement to the scorecard |
| Candidates have no visibility into where they are in the process | Candidate Experience | Candidate portal showing current stage name and estimated timeline (R2) |
| Offer negotiation is offline (back-and-forth emails) | Offer | In-platform counter-offer flow — candidate proposes adjustment, recruiter accepts/rejects (R3) |
| Onboarding checklist for new recruiter accounts | Activation | Guided onboarding checklist for first-time users (drives PLG activation metric) |
| No AI feedback on assessment quality | Assessments | After 10+ candidates take the same test, show recruiter "this question has 95% skip rate" (R3) |
| Referral program is passive (just a channel) | Sourcing | Active referral campaign: recruiter sends personalized referral request to employees per open role |

---

## Story Map Summary Table

| Activity | Steps | MVP Tasks | R2 Tasks | R3 Tasks | Total |
|---|---|---|---|---|---|
| 1. Create & Configure Job | 3 | 9 | 7 | 5 | 21 |
| 2. Publish & Attract | 3 | 8 | 6 | 3 | 17 |
| 3. Screen & Filter | 3 | 10 | 5 | 3 | 18 |
| 4. Evaluate Candidates | 4 | 17 | 10 | 5 | 32 |
| 5. Select & Offer | 3 | 10 | 6 | 2 | 18 |
| 6. Close & Learn | 2 | 4 | 5 | 4 | 13 |
| **Total** | **18** | **58** | **39** | **22** | **119** |
