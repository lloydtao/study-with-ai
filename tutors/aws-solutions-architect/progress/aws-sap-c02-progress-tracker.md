# AWS SAP-C02 Progress Tracker

Last updated: 2026-04-04

## Overall readiness snapshot

| Field | Value |
| --- | --- |
| Strongest domain | Domain 2 |
| Weakest domain | Domain 2 |
| Overdue review objectives | None |
| Next session objective set | Brief SAP-D2-O2 review, then SAP-D2-O3 |
| Notes | Second Domain 2 session completed. Storage and database tradeoff reasoning is developing well; reinforce file-storage defaults, cache boundaries, and global durable data-store choices before moving deeper into networking. |

## Domain rollups

| Domain | Total objectives | Not started | Learning | Needs review | Confident | Exam ready | Average confidence | Highest-risk objectives | Next focus |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Domain 1 | 5 | 5 | 0 | 0 | 0 | 0 | n/a | Unassessed | Wait until Unit 2 |
| Domain 2 | 5 | 3 | 2 | 0 | 0 | 0 | 3.0/5 | SAP-D2-O2 | Brief review of SAP-D2-O2, then SAP-D2-O3 |
| Domain 3 | 5 | 5 | 0 | 0 | 0 | 0 | n/a | Unassessed | Wait until Unit 3 |
| Domain 4 | 5 | 5 | 0 | 0 | 0 | 0 | n/a | Unassessed | Wait until Unit 4 |

## Objective tracker

| Objective ID | Domain | Status | Confidence | Last reviewed | Next review | Evidence | Weak points | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SAP-D1-O1 | Domain 1 | not started | - | - | - | - | - | Wait until Unit 2 |
| SAP-D1-O2 | Domain 1 | not started | - | - | - | - | - | Wait until Unit 2 |
| SAP-D1-O3 | Domain 1 | not started | - | - | - | - | - | Wait until Unit 2 |
| SAP-D1-O4 | Domain 1 | not started | - | - | - | - | - | Wait until Unit 2 |
| SAP-D1-O5 | Domain 1 | not started | - | - | - | - | - | Wait until Unit 2 |
| SAP-D2-O1 | Domain 2 | learning | 3/5 | 2026-04-04 | 2026-04-09 | Correctly added SQS buffering in front of the slow EventBridge consumer to preserve events and absorb backpressure instead of relying on direct invocation. | Still needs to state queue-per-consumer targeting, DLQs, idempotency, and direct-target vs queue-target tradeoffs more explicitly. | Revisit with one short fan-out and failure-mode scenario during the next Domain 2 session |
| SAP-D2-O2 | Domain 2 | learning | 3/5 | 2026-04-04 | 2026-04-07 | Correctly separated object storage from databases, chose Aurora/RDS for transactional order data, DynamoDB for TTL-style session data, Glacier for archival retention, and DynamoDB global tables on retry for durable low-latency multi-Region profile storage. | Needs more automatic recall on EFS vs FSx for Lustre, cache vs system-of-record decisions, and when to call out Aurora vs standard RDS or ElastiCache in front of the catalog layer. | Run a short review on storage-type defaults and cache boundaries, then continue to SAP-D2-O3 |
| SAP-D2-O3 | Domain 2 | not started | - | - | - | - | - | Continue in curriculum order |
| SAP-D2-O4 | Domain 2 | not started | - | - | - | - | - | Continue in curriculum order |
| SAP-D2-O5 | Domain 2 | not started | - | - | - | - | - | Use as cross-cutting synthesis after earlier Domain 2 objectives |
| SAP-D3-O1 | Domain 3 | not started | - | - | - | - | - | Wait until Unit 3 |
| SAP-D3-O2 | Domain 3 | not started | - | - | - | - | - | Wait until Unit 3 |
| SAP-D3-O3 | Domain 3 | not started | - | - | - | - | - | Wait until Unit 3 |
| SAP-D3-O4 | Domain 3 | not started | - | - | - | - | - | Wait until Unit 3 |
| SAP-D3-O5 | Domain 3 | not started | - | - | - | - | - | Wait until Unit 3 |
| SAP-D4-O1 | Domain 4 | not started | - | - | - | - | - | Wait until Unit 4 |
| SAP-D4-O2 | Domain 4 | not started | - | - | - | - | - | Wait until Unit 4 |
| SAP-D4-O3 | Domain 4 | not started | - | - | - | - | - | Wait until Unit 4 |
| SAP-D4-O4 | Domain 4 | not started | - | - | - | - | - | Wait until Unit 4 |
| SAP-D4-O5 | Domain 4 | not started | - | - | - | - | - | Wait until Unit 4 |
