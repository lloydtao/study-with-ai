# Study System Guide

This repository uses a markdown-first study workflow for AWS Certified Solutions Architect - Professional (SAP-C02) preparation.

## Folder roles

- `thoughts/research/` stores research notes and source summaries. These notes explain the factual basis for the study system but are not the day-to-day operating record.
- `thoughts/curriculum/` stores the canonical curriculum map and the learning objectives that define what will be studied.
- `thoughts/progress/` stores the canonical tracker and tracker template used to record current mastery, review state, and evidence.
- `thoughts/sessions/` stores dated tutoring notes from individual study sessions.

## Source of truth

- Exam scope: `thoughts/research/2026-03-28-1545-aws-solutions-architect-professional-exam-study.md`
- Curriculum objectives: `thoughts/curriculum/aws-sap-c02-curriculum-index.md` plus the domain objective files in `thoughts/curriculum/`
- Progress state: `thoughts/progress/aws-sap-c02-progress-tracker.md`
- Session history: dated session files in `thoughts/sessions/`
- Tutor workflow: `thoughts/aws-sap-c02-tutor-operating-guide.md`
- Learner baseline and preferences: `thoughts/learner-profile.md`

If a session note conflicts with the canonical tracker, update the tracker after the session and treat the tracker as the current state.

## Naming conventions

- Canonical files use stable, undated names so the tutor always knows where to look first.
- Research notes use `YYYY-MM-DD-HHMM-topic.md` so external-source investigations stay time-stamped.
- Session notes use `YYYY-MM-DD-topic.md` so review history is easy to scan chronologically.
- Objective IDs stay stable across curriculum and tracking documents and use the form `SAP-Dx-Oy`.

## Expected session flow

1. Read the curriculum index to choose the next objective.
2. Read the progress tracker to confirm current status and review needs.
3. Run or continue a dated session note in `thoughts/sessions/`.
4. Update the canonical tracker after the session finishes.
