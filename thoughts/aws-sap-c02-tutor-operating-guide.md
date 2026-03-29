# AWS SAP-C02 Tutor Operating Guide

Use this guide to run consistent AI-assisted tutoring sessions against the curriculum and tracker.

## Inputs to read before each session

1. `thoughts/curriculum/aws-sap-c02-curriculum-index.md`
2. `thoughts/progress/aws-sap-c02-progress-tracker.md`
3. The most recent relevant file in `thoughts/sessions/`
4. `thoughts/learner-profile.md`

## Objective selection rules

Choose objectives in this order:

1. Overdue review objectives with status `needs review`
2. Objectives already in `learning` that need reinforcement before adding more new material
3. The next `not started` objective in the curriculum sequence
4. Mixed-domain scenario review when at least one objective in every domain is `confident`

Keep the session focused on one primary objective and at most one secondary objective unless the learner is explicitly asking for a broader scenario drill.

## Session loop

1. Confirm the session objective and why it is next.
2. Ask a short baseline question to measure current recall.
3. Teach the concept with tradeoffs, not just service descriptions.
4. Run diagnostic questions that force comparison, prioritization, or architecture decisions.
5. Capture misunderstandings, hesitations, and missing assumptions.
6. End with a concise recap, one follow-up action, and explicit tracker updates.

## Teaching guidance

- Tie explanations back to Well-Architected tradeoffs whenever possible.
- Prefer scenario-based questions over definition recall.
- Push for comparisons such as "why this over that" when the learner answers correctly.
- If the learner is stuck, narrow the problem instead of abandoning the objective.
- If the learner is consistently strong, raise the difficulty by adding organizational, migration, cost, or resilience constraints.

## Review cadence

- Default cadence: alternate between new material and targeted review.
- If two or more objectives are marked `needs review`, spend the next session on review before introducing new content.
- Revisit a newly studied objective within 2 to 5 days.
- Revisit `needs review` objectives within 1 to 3 days.
- Revisit `confident` objectives with mixed-domain scenario practice within 7 to 14 days.

## Mastery decisions

- Move an objective from `not started` to `learning` after the first serious teaching session.
- Move an objective to `needs review` when the learner can explain parts of it but still misses important tradeoffs or failure modes.
- Move an objective to `confident` when the learner reasons through realistic scenarios with only light prompting.
- Move an objective to `exam ready` only after repeated success on time-bounded, tradeoff-heavy questions.

## Tracker update rules

- Update the canonical tracker immediately after every session.
- Add concise evidence tied to actual performance in the session.
- Record weak points as the smallest set of issues that would most likely cause an exam miss.
- Set the next review date before ending the session.

## Session note naming

- New sessions should use `thoughts/sessions/YYYY-MM-DD-topic.md`.
- If multiple sessions happen on the same day, keep the date and add a short unique topic suffix.
