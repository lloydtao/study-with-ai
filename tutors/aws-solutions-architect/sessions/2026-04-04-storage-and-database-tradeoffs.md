# AWS SAP-C02 Session Note

## Session metadata

| Field | Value |
| --- | --- |
| Date | 2026-04-04 |
| Primary objective | SAP-D2-O2 |
| Secondary objective | SAP-D2-O1 |
| Session type | New material |
| Duration | Completed async session |

## Why this session is next

- Curriculum position: Second objective in Unit 1, Domain 2: Design for New Solutions.
- Tracker reason: `SAP-D2-O2` is the next `not started` objective in sequence, and the previous session recommended a brief `SAP-D2-O1` reinforcement before continuing.
- Expected outcome: Strengthen storage and database tradeoff reasoning across relational, NoSQL, object, block, file, caching, backup, and recovery decisions while briefly reinforcing async failure-mode design.

## Baseline check

- Opening question: A global SaaS platform needs to store user-uploaded media, shared application content, transactional order data, user session state, and a low-latency product catalog that can absorb unpredictable read spikes. How would you map those needs to AWS storage and database services, and what tradeoffs would drive your choices?
- Learner starting point: Correctly separated object storage from database-backed application data and chose S3 plus CloudFront for persistent, globally distributed static media and shared content. Correctly recognized that unpredictable high-read catalog traffic often points toward DynamoDB on-demand instead of scaling relational read capacity reactively with RDS read replicas. Still needs to break the remaining workload into smaller data classes more explicitly, especially differentiating transactional order data from user session state and calling out the tradeoff boundaries where RDS or Aurora remains the stronger choice.

## Teaching notes

- Core concepts covered: Object vs block vs file storage, relational vs key-value/document databases, read/write scaling patterns, consistency and transaction boundaries, caching strategy, durability, backup and restore posture, and recovery tradeoffs.
- Tradeoffs emphasized: Operational simplicity vs control, flexible schema vs relational integrity, single-digit millisecond access vs archival economics, shared POSIX access vs application-level object access, and recovery objectives vs ongoing replication cost.
- Reference documents used: `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-2-new-solutions.md`, `tutors/aws-solutions-architect/progress/aws-sap-c02-progress-tracker.md`, `tutors/aws-solutions-architect/learner-profile.md`, `tutors/aws-solutions-architect/sessions/2026-03-29-compute-and-integration-patterns.md`

## Diagnostic questions

1. A company is modernizing an order management system. Orders require ACID guarantees and complex reporting joins, but product catalog reads are much heavier than writes and spike during launches. Which data stores and caching layers would you choose, and why?
2. A media-processing platform runs containerized workloads on ECS and needs high-performance shared access to working files during processing, durable long-term storage for uploaded assets, and cheap retention for rarely accessed originals for seven years. Which storage services fit each layer, and what tradeoffs matter?
3. A globally distributed gaming platform must store player profiles with single-digit millisecond reads worldwide, tolerate Region failure, and handle very high request volume with minimal operational overhead. Where would you start, and what design caveats would you call out?
4. Quick review from `SAP-D2-O1`: An EventBridge rule currently invokes three Lambda consumers directly. One consumer can fall behind for minutes and must not lose events if it is throttled. What change would you make, and why is that better than keeping all consumers as direct targets?

## Learner responses and observations

- Strong signals: Quickly mapped durable static assets to S3 and correctly used CloudFront as the global distribution layer. Good instinct that DynamoDB on-demand can absorb bursty catalog traffic more naturally than an RDS design that depends on scaling read replicas. On follow-up, cleanly separated orders, sessions, and catalog workloads by access pattern and consistency need: Aurora or RDS for transactional order data, DynamoDB for low-latency TTL-oriented session storage, and a conditional Aurora/RDS vs DynamoDB choice for catalog data based on query complexity. In the media scenario, correctly recognized S3 Glacier as a strong fit for low-cost long-retention storage of rarely accessed originals and showed good cost awareness around lifecycle-driven storage choices. After explanation, correctly adopted EFS as the default answer when many ECS tasks need shared working-file access during processing. In the global gaming scenario, correctly recognized that ultra-low latency and multi-Region availability matter enough to influence the primary data design rather than being afterthoughts. On retry, correctly selected DynamoDB global tables as the durable low-latency multi-Region profile store and identified data-model fit as a core caveat, with Redis framed appropriately as an optional acceleration layer rather than the system of record.
- Hesitations: Initial answer grouped order data, session data, and catalog data together before fully separating their consistency and query requirements. In the media-processing scenario, drifted from the storage question into compute optimization and treated S3 plus caching as if it covered the shared working-file requirement. In the gaming scenario, moved too quickly to Redis as the primary store without first checking whether the workload needed a durable database of record.
- Missing assumptions: Has not yet explicitly called out when a cache such as ElastiCache should sit in front of the catalog store, or the operational and feature differences between Aurora and standard RDS when selecting the relational option. Still needs more practice distinguishing EFS as the managed default from FSx for Lustre as the higher-performance specialist option. Needs firmer default mapping for globally distributed low-latency durable profile data, especially when DynamoDB global tables is a better fit than ElastiCache.

## Misunderstandings to correct

- CloudFront improves global delivery and origin offload, but S3 remains the persistence layer; the CDN does not replace storage design decisions.
- Burst-friendly reads do not make DynamoDB the right answer for every data type in the workload; the access pattern and transactional model still decide the database.
- Shared working files for containerized processing usually require a file system such as EFS or, for higher-performance HPC-style workloads, FSx for Lustre; S3 is durable object storage and is not a drop-in replacement for shared POSIX file access.
- ElastiCache/Redis is usually an acceleration layer, not the default durable globally distributed system of record for user profiles; when the question emphasizes persistent globally low-latency profile data with minimal operational overhead, DynamoDB global tables is often the stronger first answer.

## Action items

- Learner follow-up: Review the default mappings and tradeoffs for EFS vs FSx for Lustre, DynamoDB global tables vs ElastiCache, and when ElastiCache fronts a catalog store instead of replacing it.
- Tutor follow-up: Start the next session with one short `SAP-D2-O2` reinforcement question, then continue to `SAP-D2-O3` if the review is clean.

## Tracker updates

| Objective ID | Old status | New status | Confidence | Last reviewed | Next review | Evidence | Weak points | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SAP-D2-O1 | learning | learning | 3/5 | 2026-04-04 | 2026-04-09 | Correctly added SQS buffering in front of the slow EventBridge consumer to preserve events and absorb backpressure instead of relying on direct invocation. | Still should state queue-per-consumer targeting, DLQs, idempotency, and direct-target vs queue-target tradeoffs more explicitly. | Revisit with one short fan-out and failure-mode scenario during the next Domain 2 session. |
| SAP-D2-O2 | not started | learning | 3/5 | 2026-04-04 | 2026-04-07 | Correctly split object storage from databases, chose Aurora/RDS for transactional order data, DynamoDB for TTL-style session data, Glacier for low-cost archival retention, and DynamoDB global tables on retry for durable low-latency multi-Region profile storage. | Needs more automatic recall on EFS vs FSx for Lustre, cache vs system-of-record decisions, and when to call out Aurora vs standard RDS or ElastiCache in front of the catalog layer. | Run a short review on storage-type defaults and cache boundaries, then continue to `SAP-D2-O3`. |

## Next session recommendation

- Recommended objective(s): Brief review of `SAP-D2-O2`, then `SAP-D2-O3`.
- Why: The main storage and database tradeoff patterns are emerging well, but one short reinforcement pass should make the file-storage and global-data defaults more automatic before moving into networking architecture.
