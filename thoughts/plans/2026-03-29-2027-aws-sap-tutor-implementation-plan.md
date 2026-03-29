# Implementation Plan: AWS Solutions Architect Professional Tutor Workflow

## Overview

This plan covers adding a structured, markdown-first tutoring workflow to this repository so it can support ongoing preparation for the AWS Certified Solutions Architect - Professional (SAP-C02) exam. The target outcome is a reusable study system that lets an AI tutor guide sessions over time using a curriculum built from explicit learning objectives, while also tracking progress, confidence, gaps, and next steps.

The implementation should follow the repository's current shape: a lightweight notes workspace rather than an application codebase. The plan therefore assumes a documentation-first solution under `thoughts/` instead of a web app, CLI, or database-backed system.

## Current state analysis

- The repository currently contains only root metadata files plus notes directories:
  - `README.md`
  - `.gitignore`
  - `LICENSE`
  - `thoughts/research/2026-03-28-1545-aws-solutions-architect-professional-exam-study.md`
- `README.md` defines the repo purpose as "Personal study notes using LLMs as a tutor."
- There is no application code, package manifest, build tooling, study workflow, curriculum structure, tracker, session template, or exam-specific prompt/process file in the repo today.
- `thoughts/plans/` exists but is empty before this plan document.
- The existing AWS research note is the only in-repo domain artifact relevant to this task. It establishes:
  - the repo is currently a notes workspace
  - SAP-C02 domain weightings
  - core AWS reference sources for study
  - a gap between high-level research and a usable tutoring/progress workflow

## Desired end state

The repository should support an ongoing tutoring loop for SAP-C02 preparation with enough structure that future sessions can reliably continue from prior progress.

At the end of implementation, the repo should contain:

- A defined study information architecture under `thoughts/` for curriculum, tracking, and session history.
- A curriculum broken into learning objectives aligned to the SAP-C02 domains and major AWS study themes already identified in the research note.
- A progress-tracking mechanism that records status for each objective over time.
- A repeatable tutoring workflow that tells the AI tutor how to run sessions, assess readiness, revisit weak areas, and pick the next topic.
- Seed content sufficient to begin studying immediately without inventing the structure from scratch each session.

## What we are not doing

- Building a web application, dashboard, database, or custom software product.
- Adding external integrations to AWS Skill Builder, calendars, spreadsheets, or task tools.
- Attempting to mirror all AWS training content or copy official exam materials into the repo.
- Writing a full textbook for every AWS service before the workflow becomes usable.
- Automating scoring with scripts unless a later task explicitly asks for that.
- Replacing the existing research note; it should remain the factual source document that the new structure builds upon.

## Implementation approach

Use a markdown-first content architecture that fits the current repository and keeps the system easy to evolve.

Proposed approach:

1. Define a stable folder structure for exam study artifacts under `thoughts/`.
2. Convert the existing exam research into a curriculum backbone based on SAP-C02 domains and supporting themes such as Well-Architected, migration strategies, organizational complexity, resiliency, security, networking, governance, and cost/performance tradeoffs.
3. Create a learning-objective schema that is granular enough to track mastery, for example:
   - objective ID
   - domain
   - objective statement
   - status
   - confidence
   - evidence or notes
   - last reviewed date
   - next review target
4. Create a progress tracker that summarizes where the learner stands across all objectives.
5. Create tutoring/session templates so future AI-assisted study follows a consistent loop:
   - choose next objective
   - teach
   - check understanding
   - record progress
   - assign follow-up
6. Seed the initial curriculum and tracker with enough content to support immediate use, prioritizing coverage over perfect completeness.

Recommended artifact set:

- `thoughts/curriculum/` for the curriculum map and objective lists
- `thoughts/progress/` for the canonical tracker
- `thoughts/sessions/` for dated tutoring notes
- `thoughts/research/` retained for external-source research notes
- optionally a short tutor operating guide under `thoughts/` if future sessions need consistent instructions

## Phased execution plan

### Phase 1: Establish study system structure

Create the content architecture and define the role of each document so the repository has a clear source of truth.

Key work:

- Create directories for curriculum, progress, and session notes.
- Define naming conventions for dated notes and canonical tracker files.
- Decide which document is authoritative for:
  - exam scope
  - curriculum objectives
  - progress state
  - session history

Success criteria:

- The repository has a clear, durable study-note structure.
- A future tutoring session can determine where to read scope, current status, and study history without ambiguity.

### Phase 2: Design the curriculum model

Translate the SAP-C02 exam scope into a usable curriculum that is objective-driven instead of topic-list driven.

Key work:

- Create a curriculum index document that maps the four SAP-C02 domains into study units.
- Break each domain into learning objectives at a trackable level of granularity.
- Attach recommended references to each unit using the existing research note's AWS sources.
- Order objectives into a practical study sequence that balances exam weighting with prerequisite knowledge.

Success criteria:

- Every SAP-C02 domain is represented in the curriculum.
- Each study unit has explicit learning objectives rather than only broad themes.
- The curriculum is sequenced well enough to run iterative tutoring sessions.

### Phase 3: Create the progress-tracking model

Define how progress will be recorded so the tutor can adapt over time.

Key work:

- Create a canonical objective tracker template.
- Define statuses such as `not started`, `learning`, `needs review`, `confident`, and `exam ready`.
- Add fields for confidence, evidence, weak points, and next review date.
- Decide how summary rollups will work at unit and domain level.

Success criteria:

- Progress can be tracked at objective level and summarized at domain level.
- The tracker supports iterative review rather than one-time completion.
- A future tutoring session can choose the next topic from recorded state instead of guesswork.

### Phase 4: Define the tutor workflow

Specify how the AI tutor should operate against the curriculum and tracker.

Key work:

- Create a tutoring-session template with sections for:
  - objective(s) covered
  - teaching notes
  - diagnostic questions
  - misunderstandings
  - action items
  - tracker updates
- Create a lightweight operating guide for how the tutor chooses objectives, revisits weak areas, and logs outcomes.
- Define the cadence for review loops, such as new material versus spaced review.

Success criteria:

- The tutor can run repeatable sessions with consistent outputs.
- The workflow clearly connects teaching, checking understanding, and updating progress.
- Session notes can be used as evidence for mastery decisions.

### Phase 5: Seed initial content for immediate use

Populate the system enough that studying can begin right away.

Key work:

- Add the first pass of curriculum objectives across all four domains.
- Create the initial tracker file.
- Create the first session template.
- Optionally create an initial learner-profile note to capture assumptions, background, and target exam timeline if needed later.

Success criteria:

- The repository is immediately usable for the next tutoring session.
- There is enough seeded structure that future work is iterative refinement, not reinvention.

## Success criteria for each phase

- Phase 1 succeeds when the repository has an unambiguous study-system structure.
- Phase 2 succeeds when SAP-C02 scope is represented as explicit, trackable learning objectives.
- Phase 3 succeeds when mastery and review state can be recorded and summarized reliably.
- Phase 4 succeeds when the tutor has a repeatable session process tied to the tracker.
- Phase 5 succeeds when the repository contains enough initial curriculum and tracker content to begin studying immediately.

## Risks or dependencies

- Official AWS exam details may change over time, so the curriculum should cite the current research note and be easy to refresh.
- The existing research note identified some AWS Skill Builder details as not directly verifiable in the earlier environment; implementation should avoid depending on unavailable page specifics unless separately confirmed.
- Scope can expand quickly because SAP-C02 spans broad enterprise architecture topics. Objective granularity should be practical, not exhaustive.
- Without a defined learner baseline, the initial sequence may need later adjustment for prior AWS experience, weak domains, or target exam date.
- If the repository later evolves into software rather than notes, the markdown structure may need to be migrated, so file organization should stay clean and predictable.
