# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a documentation-only repository for an **AI4Devs course exercise** on Product Management and Business Analysis. There is no application code — all content is Markdown files.

The exercise asks students to act as a Product Manager/BA and produce:
1. User Stories (minimum 2, using a standard template)
2. A prioritized Product Backlog (with methodology notes)
3. Detailed work tickets for one selected User Story
4. (Optional) Effort estimation using Fibonacci, Planning Poker, or T-shirt sizes

## Repository Structure

- `ReadMe.md` — Bilingual (EN/ES) exercise instructions
- `LTI-LAOR/` — Work folder for student Luis Ovando (initials LAOR):
  - `project-brief.md` — LTI ATS project brief with hiring workflow flowchart and strategic objectives
  - `LTI-LAOR.md` — Main deliverable: full system design, user stories, backlog, and work tickets
  - `UserStories-LAOR.md` — Detailed user stories using standard template format
  - `UserStoryMap-LTI-ATS.md` — User story mapping with activities, steps, tasks, and release slices
  - `PRD-LTI-ATS.md` — Product Requirements Document with structured PRD format
  - `prompts.md` — AI prompts used to generate the content (required deliverable)

## Project Context: LTI ATS

LTI is a fictional HR tech startup building a next-generation **Applicant Tracking System (ATS)**. Key differentiators: native AI at every pipeline stage, transparent freemium pricing, and real-time collaboration. The system design covers job posting management, multichannel publishing, candidate pipeline (Kanban), assessments, smart scheduling, and analytics.

The data model targets PostgreSQL with multi-tenancy, configurable hiring pipelines, structured scorecards, AI matching scores, and an audit trail per application (12–16 entities, startup MVP scope).

## Conventions

- Each student places their work in `LTI-<INITIALS>/` with files named `UserStories-<INITIALS>.md` and `prompts.md`.
- All diagrams use Mermaid, PlantUML, or ASCII — no external tooling required.
- The `prompts.md` file must include the actual prompts used and conclusions on prompt effectiveness.
- This is a collaborative repo; changes come in via pull requests, one folder per student.
