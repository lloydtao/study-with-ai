# AWS SAP-C02 Curriculum Index

This curriculum translates the SAP-C02 exam scope into trackable learning objectives for ongoing tutoring sessions.

## Curriculum principles

- Keep objective IDs stable across curriculum, tracking, and session notes.
- Study in a sequence that builds core architecture judgment before deeper enterprise and migration scenarios.
- Use the AWS research note as the factual scope baseline and the AWS reference corpus as the preferred reading list.
- Favor mastery of tradeoffs, not memorization of isolated service facts.

## Study sequence

1. Orientation and exam framing
   - Read the research note summary, domain weights, and reference list.
   - Confirm the learner baseline in the learner profile before deep study begins.
2. Unit 1: Domain 2, Design for New Solutions
   - Start with net-new architecture design because it establishes the core tradeoff language used in the other domains.
3. Unit 2: Domain 1, Design Solutions for Organizational Complexity
   - Add enterprise governance, operating-model, and cross-account complexity after the base design patterns are in place.
4. Unit 3: Domain 3, Continuous Improvement for Existing Solutions
   - Practice reviewing and improving live systems after the target-state architecture patterns are familiar.
5. Unit 4: Domain 4, Accelerate Workload Migration and Modernization
   - Finish with migration and modernization decisions that depend on design, governance, and improvement judgment.
6. Full review loop
   - Revisit weak objectives, mixed-domain scenarios, and exam-style tradeoff questions until the tracker shows broad readiness.

## Domain map

| Unit | Domain | Weight | Objective file | Objective count |
| --- | --- | --- | --- | --- |
| 1 | Domain 2: Design for New Solutions | 29% | `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-2-new-solutions.md` | 5 |
| 2 | Domain 1: Design Solutions for Organizational Complexity | 26% | `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-1-organizational-complexity.md` | 5 |
| 3 | Domain 3: Continuous Improvement for Existing Solutions | 25% | `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-3-continuous-improvement.md` | 5 |
| 4 | Domain 4: Accelerate Workload Migration and Modernization | 20% | `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-4-migration-modernization.md` | 5 |

## Cross-cutting themes

These themes should be revisited in every unit rather than treated as one-time topics:

- AWS Well-Architected tradeoffs across security, reliability, performance efficiency, cost optimization, operational excellence, and sustainability
- Multi-account governance and organizational boundaries
- Networking and connectivity choices across VPCs, Regions, and hybrid environments
- Resiliency, disaster recovery, and failure-mode thinking
- Security, identity, logging, and compliance design
- Cost, performance, and operational complexity tradeoffs

## Recommended reference backbone

- Local scope baseline: `thoughts/research/2026-03-28-1545-aws-solutions-architect-professional-exam-study.md`
- SAP-C02 exam guide
- SAP-C02 in-scope services page
- AWS Well-Architected Framework
- AWS Architecture Center
- AWS Prescriptive Guidance
- Large migration strategies guide
- Solutions Architect learning page and ramp-up guide

## Objective ID convention

- Domain 1 objectives use `SAP-D1-O1` through `SAP-D1-O5`
- Domain 2 objectives use `SAP-D2-O1` through `SAP-D2-O5`
- Domain 3 objectives use `SAP-D3-O1` through `SAP-D3-O5`
- Domain 4 objectives use `SAP-D4-O1` through `SAP-D4-O5`
