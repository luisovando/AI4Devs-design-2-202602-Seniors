# LTI ATS — User Stories

**Author:** Luis Ovando (LAOR)  
**Date:** 2026-04-05  
**Format:** Mike Cohn user story + Gherkin acceptance criteria  
**Source documents:** PRD-LTI-ATS.md · UserStoryMap-LTI-ATS.md · LTI-LAOR.md

---

## Personas Reference

| ID | Name | Role | Key need |
|---|---|---|---|
| **Rachel** | Rachel | Recruiter at a Series A startup | Move the right candidates through fast, with zero chasing |
| **Marcus** | Marcus | Hiring Manager (Engineering / Product) | Evaluate candidates quickly without leaving his flow |
| **Ana** | Ana | HR Director / People Ops Lead | Standardize hiring across teams and measure outcomes |
| **Sam** | Sam | Candidate | Apply easily and know where they stand in the process |

---

## Epic 1 — Job Posting & Multichannel Publishing

> Enable recruiters to create, configure, and distribute job openings with minimal manual effort.

---

### US-01 — AI-Assisted Job Description

- **Summary:** Generate an inclusive, conversion-optimized job description draft with AI to save writing time

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** generate a job description draft using AI from just the job title and seniority level
- **so that** I can publish a high-quality, inclusive posting in minutes without starting from a blank page

#### Acceptance Criteria

- **Scenario:** Recruiter generates a job description draft using AI
- **Given:** I am logged into LTI ATS and have created a new job opening
- **and Given:** I have entered the job title (e.g., "Senior Backend Engineer") and seniority level (e.g., "Senior")
- **and Given:** The AI service is available
- **When:** I click "Generate with AI"
- **Then:** A complete job description draft is displayed within 10 seconds, containing a role summary, responsibilities, requirements, and benefits sections written in inclusive language (no gendered terms)

---

- **Scenario:** Recruiter edits the AI-generated description before saving
- **Given:** An AI-generated description is displayed in the editor
- **When:** I click on any section and type my changes inline
- **Then:** My edits are saved and the modified description is preserved when I navigate away and return

---

- **Scenario:** Recruiter saves a description as a reusable template
- **Given:** I have reviewed and finalized a job description
- **When:** I click "Save as template" and enter a template name
- **Then:** The template is saved under my company's template library and is available for selection when creating future job openings

---

### US-02 — Configure Knockout Questions

- **Summary:** Automatically filter unqualified candidates before manual review using knockout questions

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** define knockout questions and their disqualifying answers for a job opening
- **so that** candidates who do not meet minimum requirements are automatically filtered out before I spend time reviewing them

#### Acceptance Criteria

- **Scenario:** Recruiter adds a yes/no knockout question
- **Given:** I am configuring the application form for a job opening
- **When:** I add the question "Are you legally authorized to work in the required country?" as a yes/no knockout question and mark "No" as the disqualifying answer
- **Then:** The question appears on the candidate-facing application form, and any candidate who answers "No" is automatically moved to "Rejected" status upon submission

---

- **Scenario:** Recruiter adds a numeric knockout question
- **Given:** I am configuring knockout questions for a software engineering role
- **When:** I add "How many years of professional experience do you have with Python?" as a numeric question and set the disqualifying condition to "less than 2"
- **Then:** Candidates who enter a value below 2 are automatically rejected and the rejection reason records "Failed knockout: Python experience < 2 years"

---

- **Scenario:** Rejected candidates receive a notification
- **Given:** A candidate has submitted an application and failed one or more knockout questions
- **When:** The system processes the submission
- **Then:** The candidate receives an automated rejection email within 5 minutes, and the pipeline dashboard shows the count of auto-rejected vs. passed candidates for that job

---

### US-03 — Multichannel Job Publication

- **Summary:** Publish a job to multiple channels simultaneously to maximize candidate reach without repetition

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** publish a job opening to multiple channels in a single action
- **so that** I reach the widest qualified candidate pool without manually posting to each platform separately

#### Acceptance Criteria

- **Scenario:** Recruiter publishes to multiple channels at once
- **Given:** I have a job opening in "Draft" status with a completed description and knockout questions
- **and Given:** I have selected LinkedIn, Indeed, and the company career site as target channels
- **When:** I click "Publish"
- **Then:** The system distributes the job to all three selected channels simultaneously, and each publication shows a status of "Active" or "Pending" within 30 seconds

---

- **Scenario:** Each application records its source channel
- **Given:** A job has been published across LinkedIn and the company career site
- **When:** A candidate applies via LinkedIn and another applies via the career site
- **Then:** Each application in the pipeline shows a "Source" label (LinkedIn / Career Site) that is used in analytics reports

---

- **Scenario:** Recruiter pauses a publication on a specific channel
- **Given:** A job is actively published on three channels
- **When:** I click "Pause" on the LinkedIn publication only
- **Then:** The LinkedIn listing is deactivated but the job remains active on Indeed and the career site, and no new applications are received from LinkedIn until I resume it

---

### US-04 — Configure Hiring Pipeline

- **Summary:** Set up a custom pipeline template per role so the evaluation stages match the team's actual hiring process

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** configure the hiring pipeline stages for a job opening
- **so that** the Kanban board reflects our real process and every team member knows exactly which stage a candidate is in

#### Acceptance Criteria

- **Scenario:** Recruiter selects an existing pipeline template
- **Given:** I am creating a new job opening for an engineering role
- **and Given:** A pipeline template named "Engineering Hiring" exists with stages: Applied → Phone Screen → Technical Test → Hiring Manager Interview → Offer → Hired
- **When:** I select "Engineering Hiring" from the template dropdown
- **Then:** The pipeline is pre-populated with those six stages in the correct order, and I can proceed to publish without additional setup

---

- **Scenario:** Recruiter reorders pipeline stages
- **Given:** I am configuring a pipeline for a design role
- **When:** I drag the "Portfolio Review" stage to position it before "Hiring Manager Interview"
- **Then:** The stage order is saved and the Kanban board renders the updated sequence when the job is published

---

---

## Epic 2 — Candidate Intake & AI Screening

> Automatically process applications, parse CVs, score candidates, and detect invalid submissions so recruiters focus only on qualified profiles.

---

### US-05 — Automatic CV Parsing

- **Summary:** Populate a structured candidate profile automatically from a submitted CV to eliminate manual data entry

#### Use Case
- **As a** Rachel (Recruiter)
- **I want** submitted CVs to be automatically parsed into structured candidate profiles
- **so that** I can review candidate information immediately without spending time extracting data from documents

#### Acceptance Criteria

- **Scenario:** CV is parsed successfully on application submission
- **Given:** A candidate has submitted an application with a PDF CV attached
- **When:** The system receives the submission
- **Then:** Within 30 seconds, a candidate profile card is created and populated with: full name, email, phone, LinkedIn URL, at least one work experience entry (company, title, dates), education, and a skills list extracted from the document

---

- **Scenario:** Recruiter overrides a parsed field
- **Given:** A candidate profile has been auto-populated and one extracted field is incorrect (e.g., wrong job title)
- **When:** I click the field and type the corrected value
- **Then:** The correction is saved immediately and a "Manually edited" indicator is shown next to that field

---

- **Scenario:** Low-confidence fields are flagged for review
- **Given:** The parser could not extract a field with high confidence (e.g., ambiguous employment dates)
- **When:** The candidate profile is displayed
- **Then:** The uncertain field is highlighted with a "Review needed" badge, prompting me to verify and confirm or correct the value

---

### US-06 — AI Semantic Match Score

- **Summary:** Prioritize candidates with the best fit using an AI-generated match score with explainable reasoning

#### Use Case
- **As a** Rachel (Recruiter)
- **I want** each application to show an AI-generated match score and explanation
- **so that** I can quickly prioritize which candidates to review first and justify my shortlist to the Hiring Manager

#### Acceptance Criteria

- **Scenario:** AI match score is generated for each application
- **Given:** A new application has been received for a "Senior Backend Engineer" job
- **and Given:** The candidate profile has been parsed from their CV
- **When:** The AI scoring service processes the application
- **Then:** The candidate's pipeline card displays a score between 0 and 100, along with a short explanation listing the top 3 matching strengths (e.g., "7 years Python experience, prior fintech background, microservices expertise") and up to 2 gaps (e.g., "No Kubernetes experience mentioned")

---

- **Scenario:** Recruiter sorts pipeline by match score
- **Given:** A job has 30 applications in the "Applied" stage
- **When:** I click "Sort by: Match Score (High to Low)"
- **Then:** The candidate cards reorder with the highest-scoring candidates at the top, and the sort persists until I change it

---

- **Scenario:** Score is recalculated after job requirements are updated
- **Given:** A job's requirements section has been edited to add "Kubernetes" as a mandatory skill
- **When:** I save the updated job requirements
- **Then:** AI match scores for all existing applications in the pipeline are recalculated within 5 minutes and the updated scores are displayed

---

### US-07 — Duplicate & Blacklist Detection

- **Summary:** Automatically detect and handle duplicate applications and blacklisted candidates to keep the pipeline clean

#### Use Case
- **As a** Rachel (Recruiter)
- **I want** the system to detect duplicates and blacklisted candidates automatically on submission
- **so that** I don't waste time processing applications that should never have entered the pipeline

#### Acceptance Criteria

- **Scenario:** Duplicate application from same candidate is detected
- **Given:** A candidate with email "john.doe@email.com" already has an active application for the "Senior Backend Engineer" job
- **When:** The same email submits a second application for the same job
- **Then:** The system blocks the duplicate submission, the candidate is not added twice to the pipeline, and the existing application is flagged with a "Duplicate submission detected" note

---

- **Scenario:** Blacklisted candidate is auto-rejected silently
- **Given:** A candidate's email appears on the company's blacklist
- **When:** That candidate submits an application for any job at the company
- **Then:** The application is automatically rejected without entering the active pipeline, an internal note is added stating "Auto-rejected: candidate is blacklisted", and no rejection reason is disclosed to the candidate

---

- **Scenario:** Recruiter adds a candidate to the blacklist
- **Given:** I am viewing a candidate's profile
- **When:** I click "Add to blacklist" and confirm the action
- **Then:** The candidate is added to the company-level blacklist, their current application is marked as rejected, and future applications from that email will be auto-rejected

---

### US-08 — Candidate Pipeline View & Triage

- **Summary:** Review and triage all applications in a Kanban view so recruiters maintain a clear picture of every candidate's status

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** see all candidates organized by pipeline stage in a Kanban view
- **so that** I always know where every candidate stands and can take the next action without losing track

#### Acceptance Criteria

- **Scenario:** Recruiter views the Kanban pipeline for a job
- **Given:** A job has applications distributed across multiple stages
- **When:** I open the pipeline view for that job
- **Then:** Each pipeline stage is shown as a column, each candidate appears as a card in their current stage column, and each card shows: candidate name, AI match score, source channel, and days in current stage

---

- **Scenario:** Recruiter opens a candidate profile card
- **Given:** I am viewing the Kanban pipeline and see a candidate card I want to review
- **When:** I click the candidate card
- **Then:** A side panel opens showing: parsed CV data, match score with explanation, knockout answers, application timeline (all events with timestamps), and any internal notes previously added

---

- **Scenario:** Recruiter advances a candidate to the next stage
- **Given:** I am reviewing a candidate and want to move them forward
- **When:** I drag the candidate card to the next stage column (or click "Move to next stage")
- **Then:** The candidate's `current_stage_id` is updated, the move is recorded in their activity timeline with my name and a timestamp, and the card appears in the new column immediately

---

---

## Epic 3 — Collaborative Evaluation (Tests + Interviews + Scorecards)

> Enable structured, traceable evaluation of candidates through assessments, scheduled interviews, and standardized scorecards, with full visibility for the whole hiring team.

---

### US-09 — Send Online Assessment

- **Summary:** Evaluate candidate technical skills with an in-platform test before scheduling interviews

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** send an online assessment to a shortlisted candidate directly from the pipeline
- **so that** I can objectively evaluate technical skills early in the process and only advance candidates who meet the bar

#### Acceptance Criteria

- **Scenario:** Recruiter sends an existing assessment to a candidate
- **Given:** I am viewing a candidate in the "Screening" stage and a relevant assessment exists in the library
- **When:** I click "Send Assessment", select the "Python Backend Assessment", set a 72-hour deadline, and confirm
- **Then:** The candidate receives an email with a personalized test link, the candidate's card shows "Assessment Sent – deadline: [date]", and the assessment appears in their activity timeline

---

- **Scenario:** Candidate completes the assessment and results appear automatically
- **Given:** A candidate has received an assessment link and completed all questions before the deadline
- **When:** The candidate submits the test
- **Then:** The system scores the responses automatically, the candidate's pipeline card updates with the score (e.g., "85/100 – Passed") and pass/fail status based on the configured threshold, and I receive an in-app notification that results are ready

---

- **Scenario:** Recruiter generates an assessment with AI
- **Given:** I need an assessment for a new role and no suitable test exists in the library
- **When:** I click "Create with AI", enter "Django REST API development, 45-minute limit, 10 questions", and confirm generation
- **Then:** A draft assessment is generated with 10 questions covering the specified topic, each with multiple-choice options and a correct answer marked, and I can edit or remove individual questions before saving

---

### US-10 — Smart Interview Scheduling

- **Summary:** Schedule interviews using real-time calendar availability to eliminate back-and-forth coordination

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** schedule an interview by checking all panelists' calendar availability from within LTI ATS
- **so that** I can confirm an interview time in one step instead of sending multiple scheduling emails

#### Acceptance Criteria

- **Scenario:** Recruiter selects panelists and system reads their availability
- **Given:** I am advancing a candidate to the "Technical Interview" stage
- **and Given:** Two interviewers have connected their Google Calendar to LTI ATS
- **When:** I select both interviewers as the interview panel and click "Find availability"
- **Then:** The system displays time slots where all selected interviewers are free within the next 10 business days, showing a maximum of 10 suggested slots

---

- **Scenario:** Candidate self-schedules from available slots
- **Given:** I have selected a set of available time slots for an interview
- **When:** I click "Send self-scheduling link" and the candidate opens the link
- **Then:** The candidate sees only the slots I approved, selects one, and the confirmed interview is immediately added to all panelists' and the candidate's calendars with a video conferencing link (Google Meet or Zoom)

---

- **Scenario:** Reminder is sent 24 hours before the interview
- **Given:** An interview has been confirmed and the scheduled time is 24 hours away
- **When:** The system's scheduled notification job runs
- **Then:** All interview participants (recruiters, interviewers, and candidate) receive an email reminder with the interview details, time, and video call link

---

### US-11 — Competency-Based Scorecard Submission

- **Summary:** Capture structured post-interview feedback through scorecards to ensure every interviewer's input is recorded and traceable

#### Use Case
- **As a** Marcus (Hiring Manager / Interviewer)
- **I want to** complete a structured scorecard immediately after my interview
- **so that** my feedback is captured consistently and on time, and the team can make a data-driven hiring decision

#### Acceptance Criteria

- **Scenario:** Interviewer receives prompt to complete scorecard after interview
- **Given:** An interview I participated in is marked as "Completed"
- **When:** The interview status changes to completed
- **Then:** I receive an in-app notification and an email prompt asking me to complete the scorecard, with a direct link to the form, within 15 minutes of the interview end time

---

- **Scenario:** Interviewer submits scorecard with competency ratings and overall recommendation
- **Given:** I have opened the scorecard form for a completed interview
- **When:** I rate each competency on a 1–5 scale, add written notes per criterion, select an overall recommendation ("Strong Yes"), and click "Submit"
- **Then:** My scorecard is saved and locked, my rating is included in the decision panel immediately, and the recruiter's pending feedback tracker shows my scorecard as "Submitted"

---

- **Scenario:** Recruiter sees which interviewers have pending scorecards
- **Given:** A candidate has completed two interviews, but only one of the two interviewers has submitted a scorecard
- **When:** I open the candidate's pipeline card
- **Then:** A "Pending feedback" badge shows "1 of 2 scorecards submitted" with the name of the interviewer who has not yet completed theirs, and I can click to send them a reminder

---

### US-12 — Decision Panel Review

- **Summary:** Give the Hiring Manager a consolidated view of all interview feedback to make the final candidate decision quickly and with confidence

#### Use Case
- **As a** Marcus (Hiring Manager)
- **I want to** see all interviewer scorecards consolidated in a single panel for a candidate
- **so that** I can make a fast, well-informed final hiring decision without having to chase individual interviewers for their opinions

#### Acceptance Criteria

- **Scenario:** Hiring Manager views consolidated decision panel
- **Given:** All interviewers for a candidate have submitted their scorecards
- **When:** I open the decision panel for that candidate
- **Then:** I see all scorecards displayed side by side with: each interviewer's name, their per-competency ratings, their notes, and their overall recommendation; plus a summary row showing the average score per competency and the recommendation distribution (e.g., "3 Strong Yes, 1 Yes, 0 No")

---

- **Scenario:** Hiring Manager records a final decision
- **Given:** I have reviewed the consolidated panel for a finalist candidate
- **When:** I select "Advance to Offer" and add a decision note ("Strong technical performance, culture fit confirmed")
- **Then:** The candidate is moved to the "Offer" stage, my decision note and timestamp are recorded in the candidate's activity timeline, and the recruiter receives an in-app notification to proceed with the offer

---

### US-13 — AI-Assisted Interview Summary

- **Summary:** Reduce the time interviewers spend writing notes by generating an AI summary from raw interview notes

#### Use Case
- **As a** Marcus (Hiring Manager / Interviewer)
- **I want** the system to generate a summary of my interview notes automatically
- **so that** I can complete my scorecard faster and spend less time on administrative write-up

#### Acceptance Criteria

- **Scenario:** AI generates a summary from submitted interview notes
- **Given:** I have written free-form notes during an interview (minimum 100 words)
- **and Given:** The AI summarization feature is available on my plan
- **When:** I click "Summarize with AI" before submitting the scorecard
- **Then:** A structured 3–5 sentence summary of the candidate's key strengths, concerns, and notable moments is generated and inserted into the "Notes" field of the scorecard, which I can edit before submitting

---

---

## Epic 4 — Offer & Hiring

> Close the process by generating compliant offer letters, collecting e-signatures, and managing rejections — all from within LTI ATS.

---

### US-14 — Offer Letter Generation & E-Signature

- **Summary:** Generate and send a structured offer letter for e-signature to close the hire without leaving the platform

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** generate an offer letter from a template and send it for e-signature directly from LTI ATS
- **so that** I can close the hire quickly without switching to Word documents, email attachments, and separate e-signature tools

#### Acceptance Criteria

- **Scenario:** Recruiter generates an offer letter from a template
- **Given:** A candidate has been moved to the "Offer" stage after the Hiring Manager's final decision
- **When:** I click "Generate Offer", select the "Full-Time Engineering Offer" template, enter salary ($120,000), currency (USD), benefits package ("Standard + Stock options"), and start date (2026-05-01), and click "Generate"
- **Then:** A formatted PDF offer letter is generated with all entered values embedded, and I can preview it before sending

---

- **Scenario:** Offer is sent to candidate for e-signature
- **Given:** I have previewed and approved the generated offer PDF
- **When:** I click "Send for Signature"
- **Then:** The candidate receives an email with the offer letter and an e-signature request link; the offer status updates to "Sent"; and the timestamp is recorded in the candidate's activity timeline

---

- **Scenario:** Candidate accepts by signing electronically
- **Given:** The candidate has opened the offer link and reviewed the document
- **When:** The candidate adds their electronic signature and clicks "Accept"
- **Then:** The offer status updates to "Accepted", the candidate's application status changes to "Hired", I receive an immediate in-app and email notification, and the signed document URL is stored in the candidate's profile

---

- **Scenario:** Automatic reminder is sent for unsigned offers
- **Given:** An offer was sent 3 days ago and the candidate has not yet signed
- **When:** The system's daily reminder job runs
- **Then:** The candidate receives an automated follow-up email with the original signing link, and the offer activity timeline shows "Reminder sent on [date]"

---

### US-15 — Candidate Rejection & Talent Pool Archiving

- **Summary:** Reject candidates at any stage with optional talent pool archiving so strong profiles aren't lost for future openings

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** reject a candidate and optionally add them to the talent pool with descriptive tags
- **so that** strong candidates who aren't the right fit now are available for future roles without having to start from scratch

#### Acceptance Criteria

- **Scenario:** Recruiter rejects a candidate and sends a rejection notification
- **Given:** I am viewing a candidate in the pipeline who will not advance
- **When:** I click "Reject", select a rejection reason from the dropdown (e.g., "Overqualified"), and click "Confirm"
- **Then:** The candidate's status is updated to "Rejected", they are removed from the active pipeline view, and they receive a rejection email using the company's configured rejection template within 5 minutes

---

- **Scenario:** Recruiter adds a rejected candidate to the talent pool with tags
- **Given:** I am rejecting a strong candidate who is not the right fit for this specific role
- **When:** During the rejection flow, I toggle "Add to Talent Pool", add tags ("senior backend", "future team lead", "strong systems design"), and confirm
- **Then:** The candidate is added to the company talent pool with the specified tags, and the rejection confirmation shows "Added to talent pool: senior backend, future team lead, strong systems design"

---

- **Scenario:** Recruiter finds a talent pool candidate for a new opening
- **Given:** A new "Staff Backend Engineer" job has been created
- **When:** I open the Talent Pool, filter by tag "senior backend", and find the previously rejected candidate
- **Then:** I can click "Add to Pipeline" to move them directly into the new job's pipeline at the "Screening" stage without requiring a new application submission

---

### US-16 — Close Job & Process Wrap-Up

- **Summary:** Formally close a filled job, notify all remaining candidates, and trigger HRIS handoff to complete the hiring lifecycle

#### Use Case
- **As a** Rachel (Recruiter)
- **I want to** close a job after a successful hire with a single action that handles all remaining notifications and handoffs
- **so that** the process ends cleanly, every candidate receives a status update, and the new hire's data reaches the HRIS without manual export

#### Acceptance Criteria

- **Scenario:** Job is closed after offer acceptance
- **Given:** A candidate has accepted an offer and their status is "Hired"
- **When:** I click "Close Job"
- **Then:** All active publications (LinkedIn, Indeed, career site) are deactivated, the job status changes to "Closed", and all remaining pipeline candidates with "Active" status receive a rejection email using the bulk rejection template

---

- **Scenario:** Hired candidate data is exported for HRIS handoff
- **Given:** A job has been closed and a candidate is marked as "Hired"
- **When:** The job is closed
- **Then:** A structured data export (CSV or JSON) is generated containing the hired candidate's name, email, job title, department, start date, and salary, available for manual download or API-based HRIS import

---

---

## Epic 5 — Analytics & Reporting

> Provide actionable dashboards and proactive alerts that help recruiters and HR leaders optimize the hiring process over time.

---

### US-17 — Time-to-Hire Dashboard

- **Summary:** Give HR leaders real-time visibility into hiring performance and bottlenecks to make data-driven process improvements

#### Use Case
- **As an** Ana (HR Director)
- **I want to** see a real-time dashboard showing time-to-fill, pipeline conversion rates, and source effectiveness
- **so that** I can identify where the hiring process is slowing down and take corrective action before good candidates drop off

#### Acceptance Criteria

- **Scenario:** Ana views company-wide time-to-fill metrics
- **Given:** My company has at least 3 closed jobs in the system
- **When:** I open the Analytics dashboard
- **Then:** I see: average time-to-fill (in calendar days) across all closed jobs, broken down by department and individual job; median time-to-fill; and a trend line comparing the last 3 months

---

- **Scenario:** Ana views stage-level conversion rates
- **Given:** I am viewing the Analytics dashboard for a specific job
- **When:** I navigate to the "Pipeline Funnel" section
- **Then:** I see the number of candidates who entered each stage and the percentage who advanced to the next stage (e.g., "Applied: 120 → Screening: 45 (37.5%) → Test: 30 (66.7%) → Interview: 18 (60%) → Offer: 3 (16.7%) → Hired: 2 (66.7%)")

---

- **Scenario:** Proactive bottleneck alert fires when candidates are idle
- **Given:** A job has 5 candidates who have been in the "Technical Interview" stage for more than 5 days without any activity
- **When:** The system's daily alert check runs
- **Then:** I receive an in-app notification and email: "Bottleneck alert: 5 candidates have been in 'Technical Interview' for over 5 days on [Job Title]. Take action."

---

### US-18 — Source Effectiveness Report

- **Summary:** Show which sourcing channels produce the most and best hires so recruiters can focus their budget and effort

#### Use Case
- **As a** Ana (HR Director / People Ops Lead)
- **I want to** see a breakdown of application volume and hire rate by sourcing channel
- **so that** I can invest recruiting budget in the channels that deliver the best results and cut underperforming ones

#### Acceptance Criteria

- **Scenario:** Ana views source effectiveness metrics
- **Given:** My company has received applications from at least 3 channels (e.g., LinkedIn, Indeed, career site) over the last 90 days
- **When:** I open the "Source Effectiveness" section of the Analytics dashboard
- **Then:** I see a table listing each channel with: total applications received, number advanced past screening, number of offers made, number hired, and hire rate percentage (hired / total applications)

---

- **Scenario:** Ana filters source report by date range
- **Given:** I am viewing the source effectiveness report
- **When:** I change the date range filter from "All time" to "Last 30 days"
- **Then:** All metrics in the report update to reflect only applications received within the selected period, within 3 seconds

---

---

## Epic 6 — Account Setup & PLG Activation

> Enable a new recruiter to self-onboard and publish their first job in under 60 minutes without external help.

---

### US-19 — Self-Service Account Setup & Onboarding Checklist

- **Summary:** Guide a new recruiter through initial setup so they can publish their first job without needing support

#### Use Case
- **As a** Rachel (Recruiter) signing up for the first time
- **I want to** complete a guided setup checklist after creating my account
- **so that** I can publish my first job opening confidently without reading documentation or contacting support

#### Acceptance Criteria

- **Scenario:** New user sees guided onboarding checklist on first login
- **Given:** I have created a new LTI ATS account and log in for the first time
- **When:** The dashboard loads
- **Then:** A setup checklist modal is displayed with 4 steps: "1. Complete your company profile", "2. Invite your first team member", "3. Create your first job opening", "4. Publish your job", with each step showing as incomplete

---

- **Scenario:** Checklist step is marked complete as user progresses
- **Given:** I have completed the "Create your first job opening" step by saving a job in draft status
- **When:** I return to the dashboard
- **Then:** Step 3 of the checklist shows a checkmark and the progress bar advances from 50% to 75%

---

- **Scenario:** User dismisses checklist and it does not reappear
- **Given:** The onboarding checklist is displayed on my dashboard
- **When:** I click "Dismiss" and confirm
- **Then:** The checklist is hidden and does not reappear on subsequent logins; I can re-access it at any time from the "Help" menu under "Setup guide"

---

### US-20 — Role-Based Access & Team Invitation

- **Summary:** Invite team members with the right roles so everyone has access to the tools they need and nothing more

#### Use Case
- **As a** Rachel (Recruiter / Admin)
- **I want to** invite Hiring Managers and Interviewers to LTI ATS and assign them specific roles
- **so that** each person sees only what they need and the hiring process stays secure and traceable

#### Acceptance Criteria

- **Scenario:** Admin invites a new team member with a specific role
- **Given:** I am the account admin and I navigate to "Team Settings"
- **When:** I enter a new team member's email address, select the role "Interviewer", and click "Send Invitation"
- **Then:** The invitee receives an email with a sign-up link that grants access to the Interviewer role only; the team settings page shows their status as "Invitation Pending"

---

- **Scenario:** Invitee completes sign-up and gains role-appropriate access
- **Given:** I received an invitation email for the "Interviewer" role
- **When:** I click the link, set my password, and log in
- **Then:** I can see only the candidates assigned to my interviews, access scorecard forms, and view the interview schedule — but I cannot create job openings, reject candidates, or access analytics

---

---

## Prioritization Framework

**Framework chosen: MoSCoW** — selected for pre-PMF startup context (no usage metrics yet, small team, ruthless focus needed). Forces hard Must/Should/Could cuts without requiring data that doesn't exist yet. Maps directly to release slices R1/R2/R3.

**Fibonacci effort estimation** applied to all stories (scale: 1, 2, 3, 5, 8, 13…). Linear estimate scale caps at 8; stories estimated at 13 points are split into sub-tasks of 3–5 pts each (see splits below).

**MoSCoW → Linear priority mapping:**

| MoSCoW | Linear Priority | Meaning |
|---|---|---|
| Must | Urgent | Launch-blocking; product doesn't work without it |
| Should | High | Important but not launch-blocking |
| Could | Medium | Defer if pressured; nice to have |
| Won't | Low | Explicitly out of scope this cycle |

---

## Backlog Summary

> Stories marked **[split]** have been decomposed into 3–5 pt sub-tasks in Linear (AI4-25 to AI4-36).

| Story | Epic | Persona | MoSCoW | Pts | Linear |
|---|---|---|---|---|---|
| US-01 — AI-Assisted Job Description | Job Posting | Rachel | **Must** | 8 | AI4-5 |
| US-02 — Configure Knockout Questions | Job Posting | Rachel | **Must** | 3 | AI4-6 |
| US-03 — Multichannel Job Publication **[split]** | Job Posting | Rachel | **Must** | 13 | AI4-7 |
| ↳ US-03a — Career Site & Job Portal Publication | Job Posting | Rachel | Must | 3 | AI4-25 |
| ↳ US-03b — LinkedIn Job Board Integration | Job Posting | Rachel | Must | 5 | AI4-26 |
| ↳ US-03c — Indeed Integration & Source Attribution | Job Posting | Rachel | Should | 5 | AI4-27 |
| US-04 — Configure Hiring Pipeline | Job Posting | Rachel | **Must** | 5 | AI4-8 |
| US-05 — Automatic CV Parsing | Candidate Intake | Rachel | **Must** | 8 | AI4-9 |
| US-06 — AI Semantic Match Score **[split]** | Candidate Intake | Rachel | **Must** | 13 | AI4-10 |
| ↳ US-06a — Embedding Generation Pipeline & Vector Storage | Candidate Intake | Rachel | Must | 5 | AI4-28 |
| ↳ US-06b — Match Score Computation & Candidate Card Display | Candidate Intake | Rachel | Must | 5 | AI4-29 |
| ↳ US-06c — Score Sorting & Recalculation on Requirements Update | Candidate Intake | Rachel | Should | 3 | AI4-30 |
| US-07 — Duplicate & Blacklist Detection | Candidate Intake | Rachel | **Must** | 5 | AI4-11 |
| US-08 — Candidate Pipeline View & Triage | Candidate Intake | Rachel | **Must** | 8 | AI4-12 |
| US-09 — Send Online Assessment | Evaluation | Rachel | **Could** | 8 | AI4-13 |
| US-10 — Smart Interview Scheduling **[split]** | Evaluation | Rachel | **Must** | 13 | AI4-14 |
| ↳ US-10a — Calendar OAuth & Availability Aggregation | Evaluation | Rachel | Must | 5 | AI4-31 |
| ↳ US-10b — Candidate Self-Scheduling Link & Calendar Event Creation | Evaluation | Rachel | Must | 5 | AI4-32 |
| ↳ US-10c — Interview Reminders & Notification Flow | Evaluation | Rachel | Should | 3 | AI4-33 |
| US-11 — Competency-Based Scorecard | Evaluation | Marcus | **Must** | 5 | AI4-15 |
| US-12 — Decision Panel Review | Evaluation | Marcus | **Must** | 5 | AI4-16 |
| US-13 — AI-Assisted Interview Summary | Evaluation | Marcus | **Could** | 8 | AI4-17 |
| US-14 — Offer Letter Generation & E-Signature **[split]** | Offer & Hiring | Rachel | **Must** | 13 | AI4-18 |
| ↳ US-14a — Offer Letter Template Engine & PDF Generation | Offer & Hiring | Rachel | Must | 5 | AI4-34 |
| ↳ US-14b — E-Signature Flow & Offer Delivery | Offer & Hiring | Rachel | Must | 5 | AI4-35 |
| ↳ US-14c — Offer Status Tracking, Reminders & Expiry | Offer & Hiring | Rachel | Should | 3 | AI4-36 |
| US-15 — Candidate Rejection & Talent Pool | Offer & Hiring | Rachel | **Must** | 5 | AI4-19 |
| US-16 — Close Job & Process Wrap-Up | Offer & Hiring | Rachel | **Could** | 8 | AI4-20 |
| US-17 — Time-to-Hire Dashboard | Analytics | Ana | **Should** | 8 | AI4-21 |
| US-18 — Source Effectiveness Report | Analytics | Ana | **Could** | 5 | AI4-22 |
| US-19 — Self-Service Onboarding Checklist | Activation | Rachel | **Must** | 5 | AI4-23 |
| US-20 — Role-Based Access & Team Invitation | Activation | Rachel | **Must** | 8 | AI4-24 |

**Total Must points (R1 MVP):** 108 pts across 20 deliverables (16 stories + 4 Must sub-tasks replacing split parents)
**Total Should points (R2):** 19 pts — US-03c, US-06c, US-10c, US-14c, US-17
**Total Could points (R3):** 21 pts — US-09, US-13, US-16, US-18
