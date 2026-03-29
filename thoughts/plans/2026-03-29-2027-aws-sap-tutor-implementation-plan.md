# Implementation Plan: AWS Solutions Architect Professional Tutor Workflow

## Overview

This plan covers adding a structured, markdown-first tutoring workflow to this repository so it can support ongoing preparation for the AWS Certified Solutions Architect - Professional (SAP-C02) exam. The target outcome is a reusable study system that lets an AI tutor guide sessions over time using a curriculum built from explicit learning objectives, while also tracking progress, confidence, gaps, and next steps.

The implementation should follow the repository's current shape: a lightweight notes workspace rather than an application codebase. The plan therefore assumes a documentation-first solution, but with a clearer separation of concerns:

- `thoughts/` is reserved for cross-tutor `research/` and `plans/`
- tutor-specific operating content lives under `tutors/`
- all AWS SAP study materials live under `tutors/aws-solutions-architect/`

## Implementation progress

Last updated: 2026-03-29

- Phase 1 status: Completed
- Phase 2 status: Completed
- Phase 3 status: Completed
- Phase 4 status: Completed
- Phase 5 status: Completed
- `tutors/` and `tutors/aws-solutions-architect/` have been established as the canonical tutor namespace.
- Shared guidance in `thoughts/README.md` now reserves `thoughts/` for shared `research/` and `plans/`.
- AWS SAP curriculum, progress, session, and workflow artifacts have been moved under `tutors/aws-solutions-architect/`.
- Curriculum references, tracker references, and workflow paths have been updated to the new canonical namespace.
- Validation confirmed five curriculum files, stable objective IDs `SAP-D1-O1` through `SAP-D4-O5`, the required tutoring-session template sections, and a clean shared `thoughts/` layout.
- The AWS SAP tutor can now start the next session from `tutors/aws-solutions-architect/` without relying on deprecated operating paths.
- Existing AWS SAP content has already been drafted, but it is currently split across legacy paths under `thoughts/`.
- The updated requirement changes the target information architecture:
  - `thoughts/` should contain only shared `research/` and `plans/`
  - AWS SAP curriculum, progress, session, and workflow artifacts should be consolidated under `tutors/aws-solutions-architect/`
- The remaining work is therefore primarily namespace alignment, migration of canonical paths, and validation that the tutoring workflow still works cleanly after relocation.

## Current state analysis

- The repository is still a notes workspace rather than an application codebase.
- `thoughts/research/` and `thoughts/plans/` exist and are the right home for shared research and implementation planning.
- AWS SAP operating artifacts already exist, but they currently live in legacy locations such as:
  - `thoughts/curriculum/`
  - `thoughts/progress/`
  - `thoughts/sessions/`
  - `thoughts/aws-sap-c02-tutor-operating-guide.md`
  - `thoughts/learner-profile.md`
- There is also a partial, currently unused namespace at `thoughts/aws-solutions-architect/` with empty subdirectories.
- No `tutors/` directory exists yet, so the requested multi-tutor namespace has not been established.
- The existing AWS research note remains the key factual source document:
  - `thoughts/research/2026-03-28-1545-aws-solutions-architect-professional-exam-study.md`
- The main gap is now structural rather than conceptual: the content exists, but the canonical locations need to be reorganized so future tutors can coexist cleanly.

## Desired end state

The repository should support an ongoing tutoring loop for SAP-C02 preparation with enough structure that future sessions can reliably continue from prior progress.

At the end of implementation, the repo should contain:

- A shared notes area where `thoughts/` contains only:
  - `thoughts/research/`
  - `thoughts/plans/`
- A tutor namespace at `tutors/aws-solutions-architect/` that contains the SAP-C02 curriculum, tracker, session history, tutor workflow, and learner profile.
- A curriculum broken into learning objectives aligned to the SAP-C02 domains and major AWS study themes already identified in the research note.
- A progress-tracking mechanism that records status for each objective over time.
- A repeatable tutoring workflow that tells the AI tutor how to run sessions, assess readiness, revisit weak areas, and pick the next topic.
- Seed content sufficient to begin studying immediately without inventing the structure from scratch each session.
- A structure that can later support additional tutor namespaces under `tutors/` without mixing their operating files into `thoughts/`.

## What we are not doing

- Building a web application, dashboard, database, or custom software product.
- Adding external integrations to AWS Skill Builder, calendars, spreadsheets, or task tools.
- Attempting to mirror all AWS training content or copy official exam materials into the repo.
- Writing a full textbook for every AWS service before the workflow becomes usable.
- Automating scoring with scripts unless a later task explicitly asks for that.
- Replacing the existing research note; it should remain the factual source document that the new structure builds upon.
- Turning `thoughts/` into the home for tutor-specific curriculum, progress, or session files.

## Implementation approach

Use a markdown-first content architecture that fits the current repository and keeps the system easy to evolve.

Proposed approach:

1. Reserve `thoughts/` for shared `research/` and `plans/`, and create `tutors/aws-solutions-architect/` as the canonical home for AWS SAP operating artifacts.
2. Consolidate the existing AWS SAP materials into that tutor namespace instead of keeping them spread across top-level `thoughts/` folders.
3. Preserve the existing curriculum model and learning-objective schema so relocation does not cause unnecessary content churn. The schema should remain granular enough to track mastery, for example:
   - objective ID
   - domain
   - objective statement
   - status
   - confidence
   - evidence or notes
   - last reviewed date
   - next review target
4. Keep a canonical progress tracker that summarizes where the learner stands across all objectives.
5. Keep tutoring/session templates so future AI-assisted study follows a consistent loop:
   - choose next objective
   - teach
   - check understanding
   - record progress
   - assign follow-up
6. Update all canonical-path references so the tutor can reliably navigate between shared research in `thoughts/` and tutor-specific content in `tutors/aws-solutions-architect/`.

Recommended artifact set:

- `thoughts/research/` retained for external-source research notes
- `thoughts/plans/` retained for implementation and design plans
- `tutors/aws-solutions-architect/curriculum/` for the curriculum map and objective lists
- `tutors/aws-solutions-architect/progress/` for the canonical tracker
- `tutors/aws-solutions-architect/sessions/` for dated tutoring notes
- `tutors/aws-solutions-architect/aws-sap-c02-tutor-operating-guide.md` for workflow instructions
- `tutors/aws-solutions-architect/learner-profile.md` for learner context and preferences
- optionally `tutors/aws-solutions-architect/README.md` if a tutor-local index is useful for navigation

## Phased execution plan

### Phase 1: Establish shared-versus-tutor structure

Create the top-level information architecture so `thoughts/` and `tutors/` have clearly separated responsibilities.

Key work:

- Reserve `thoughts/` for `research/` and `plans/` only.
- Create `tutors/` and `tutors/aws-solutions-architect/` as the AWS SAP namespace.
- Define naming conventions for canonical tutor files and dated session notes.
- Decide which document is authoritative for:
  - exam scope
  - curriculum objectives
  - progress state
  - session history

Success criteria:

- The repository has a clear, durable shared-versus-tutor structure.
- A future tutoring session can determine where to read shared research versus tutor-specific operating state without ambiguity.

### Phase 2: Migrate and normalize AWS SAP artifacts

Move the existing AWS SAP materials into the new tutor namespace and preserve their roles as canonical documents.

Key work:

- Move curriculum files into `tutors/aws-solutions-architect/curriculum/`.
- Move progress artifacts into `tutors/aws-solutions-architect/progress/`.
- Move session templates and future session history into `tutors/aws-solutions-architect/sessions/`.
- Move the tutor operating guide and learner profile into `tutors/aws-solutions-architect/`.
- Remove or retire legacy AWS SAP operating paths under `thoughts/` once canonical replacements exist.

Success criteria:

- All AWS SAP operating artifacts live under `tutors/aws-solutions-architect/`.
- `thoughts/` no longer contains AWS SAP curriculum, progress, session, or workflow files outside `research/` and `plans/`.
- The repository has one unambiguous canonical path for each AWS SAP document type.

### Phase 3: Revalidate the curriculum model in its new namespace

Confirm that the existing curriculum still works cleanly after relocation and remains tied to the research note.

Key work:

- Ensure the curriculum index and all four domain files remain intact under the tutor namespace.
- Keep stable objective IDs `SAP-D1-O1` through `SAP-D4-O5`.
- Keep recommended references tied back to the shared research note in `thoughts/research/`.
- Verify the study sequence still supports iterative tutoring sessions.

Success criteria:

- Every SAP-C02 domain remains represented in the namespaced curriculum.
- Each study unit still has explicit learning objectives rather than only broad themes.
- The curriculum remains sequenced well enough to run iterative tutoring sessions from the new location.

### Phase 4: Revalidate tracking and tutor workflow

Ensure the progress model and tutor operating process still work after the namespace change.

Key work:

- Confirm the canonical objective tracker and tracker template live under `tutors/aws-solutions-architect/progress/`.
- Confirm the tutoring-session template lives under `tutors/aws-solutions-architect/sessions/` with sections for:
  - objective(s) covered
  - teaching notes
  - diagnostic questions
  - misunderstandings
  - action items
  - tracker updates
- Confirm the operating guide explains how the tutor chooses objectives, revisits weak areas, and logs outcomes from the new canonical paths.
- Update any cross-references that still point to legacy `thoughts/` operating paths.

Success criteria:

- Progress can still be tracked at objective level and summarized at domain level.
- The tutor can still run repeatable sessions with consistent outputs.
- Session notes can still be used as evidence for mastery decisions without path ambiguity.

### Phase 5: Confirm immediate usability and future extensibility

Confirm the AWS SAP tutor can be used immediately and that the repository is ready for additional tutor namespaces later.

Key work:

- Verify the migrated curriculum, tracker, session template, operating guide, and learner profile are all in place.
- Verify the AWS SAP tutor can start a new study session without relying on deprecated paths.
- Leave `thoughts/` clean enough that future tutors can follow the same pattern under `tutors/<tutor-name>/`.

Success criteria:

- The repository is immediately usable for the next AWS SAP tutoring session.
- Future tutor implementations can be added without restructuring `thoughts/` again.
- Further work becomes iterative refinement inside a stable multi-tutor layout rather than another architecture change.

## Success criteria for each phase

- Phase 1 succeeds when `thoughts/` and `tutors/` have unambiguous responsibilities.
- Phase 2 succeeds when every AWS SAP operating artifact has one canonical home under `tutors/aws-solutions-architect/`.
- Phase 3 succeeds when SAP-C02 scope remains represented as explicit, trackable learning objectives in the new namespace.
- Phase 4 succeeds when mastery, review state, and repeatable tutor workflow still function reliably after relocation.
- Phase 5 succeeds when the AWS SAP tutor is immediately usable and the repository is ready for more tutor namespaces without structural rework.

## Risks or dependencies

- Official AWS exam details may change over time, so the curriculum should cite the current research note and be easy to refresh.
- The existing research note identified some AWS Skill Builder details as not directly verifiable in the earlier environment; implementation should avoid depending on unavailable page specifics unless separately confirmed.
- Scope can expand quickly because SAP-C02 spans broad enterprise architecture topics. Objective granularity should be practical, not exhaustive.
- Without a defined learner baseline, the initial sequence may need later adjustment for prior AWS experience, weak domains, or target exam date.
- Relative links and source-of-truth references will need careful updates during migration so the tutor does not follow stale `thoughts/` paths.
- If the repository later evolves into software rather than notes, the markdown structure may need to be migrated, so file organization should stay clean and predictable.
