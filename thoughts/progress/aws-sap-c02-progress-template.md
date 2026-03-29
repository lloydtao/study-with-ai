# AWS SAP-C02 Progress Tracker Template

Use this file as the template for the canonical progress tracker.

## Status definitions

| Status | Meaning |
| --- | --- |
| `not started` | The objective has not been studied yet. |
| `learning` | The objective has been introduced, but the learner still needs guided practice. |
| `needs review` | The learner can discuss the objective but still shows important gaps, hesitation, or inconsistency. |
| `confident` | The learner can reason through most scenarios accurately with limited support. |
| `exam ready` | The learner can handle realistic tradeoff questions quickly and consistently. |

## Confidence scale

| Score | Meaning |
| --- | --- |
| 1 | Minimal familiarity |
| 2 | Partial understanding |
| 3 | Functional but inconsistent |
| 4 | Strong understanding |
| 5 | Reliable under exam-style pressure |

## Update rules

- Update the canonical tracker after every study session.
- Keep one row per objective ID.
- Use the `weak points` field for the most likely failure modes, not full session transcripts.
- Use the `evidence` field for concise proof such as scenario performance, explanations given, or follow-up completed.
- Advance an objective to `exam ready` only when the learner demonstrates consistent tradeoff reasoning without heavy prompting.

## Rollup model

- Unit rollups and domain rollups are the same because each study unit maps directly to one SAP-C02 domain.
- Each domain summary should track:
  - total objectives
  - count in each status
  - average confidence
  - highest-risk objectives
  - next recommended focus
- The overall readiness snapshot should summarize:
  - strongest domain
  - weakest domain
  - overdue review objectives
  - next session objective set

## Template structure

### Overall readiness snapshot

| Field | Value |
| --- | --- |
| Strongest domain | |
| Weakest domain | |
| Overdue review objectives | |
| Next session objective set | |
| Notes | |

### Domain rollups

| Domain | Total objectives | Not started | Learning | Needs review | Confident | Exam ready | Average confidence | Highest-risk objectives | Next focus |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Domain 1 | | | | | | | | | |
| Domain 2 | | | | | | | | | |
| Domain 3 | | | | | | | | | |
| Domain 4 | | | | | | | | | |

### Objective tracker

| Objective ID | Domain | Status | Confidence | Last reviewed | Next review | Evidence | Weak points | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SAP-D1-O1 | Domain 1 | | | | | | | |
| SAP-D1-O2 | Domain 1 | | | | | | | |
| SAP-D1-O3 | Domain 1 | | | | | | | |
| SAP-D1-O4 | Domain 1 | | | | | | | |
| SAP-D1-O5 | Domain 1 | | | | | | | |
| SAP-D2-O1 | Domain 2 | | | | | | | |
| SAP-D2-O2 | Domain 2 | | | | | | | |
| SAP-D2-O3 | Domain 2 | | | | | | | |
| SAP-D2-O4 | Domain 2 | | | | | | | |
| SAP-D2-O5 | Domain 2 | | | | | | | |
| SAP-D3-O1 | Domain 3 | | | | | | | |
| SAP-D3-O2 | Domain 3 | | | | | | | |
| SAP-D3-O3 | Domain 3 | | | | | | | |
| SAP-D3-O4 | Domain 3 | | | | | | | |
| SAP-D3-O5 | Domain 3 | | | | | | | |
| SAP-D4-O1 | Domain 4 | | | | | | | |
| SAP-D4-O2 | Domain 4 | | | | | | | |
| SAP-D4-O3 | Domain 4 | | | | | | | |
| SAP-D4-O4 | Domain 4 | | | | | | | |
| SAP-D4-O5 | Domain 4 | | | | | | | |
