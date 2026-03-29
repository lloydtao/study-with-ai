# AWS SAP-C02 Session Note

## Session metadata

| Field | Value |
| --- | --- |
| Date | 2026-03-29 |
| Primary objective | SAP-D2-O1 |
| Secondary objective | None |
| Session type | New material |
| Duration | Completed async session |

## Why this session is next

- Curriculum position: First objective in Unit 1, Domain 2: Design for New Solutions.
- Tracker reason: `SAP-D2-O1` is the next objective marked to start, and there are no overdue review items.
- Expected outcome: Build first-pass judgment for choosing compute and integration patterns based on scale, latency, and operational overhead.

## Baseline check

- Opening question: For a new AWS workload, how would you choose between Lambda, ECS/Fargate, and EC2, and when would you add SQS, EventBridge, or Step Functions instead of keeping everything synchronous?
- Learner starting point: Correctly identified EC2 as strong for steady load and stateful or long-running workloads, Lambda as a strong fit for bursty stateless short-running tasks, and Fargate as paying more to reduce infrastructure management overhead for containerized applications. Partial understanding of asynchronous integration patterns: understands SQS as a buffer for decoupling and resilience, but is unsure how EventBridge differs from SQS and why Step Functions helps in async workflows.

## Teaching notes

- Core concepts covered: Compute selection based on execution model, scaling behavior, statefulness, startup profile, runtime control, and team operating model; integration choices for decoupling, fan-out, retries, ordering, orchestration, and backpressure.
- Tradeoffs emphasized: Speed vs control, elasticity vs predictability, synchronous latency vs asynchronous resilience, orchestration clarity vs implementation simplicity, and lower ops effort vs tighter customization.
- Reference documents used: `tutors/aws-solutions-architect/curriculum/aws-sap-c02-domain-2-new-solutions.md`, `tutors/aws-solutions-architect/progress/aws-sap-c02-progress-tracker.md`, `tutors/aws-solutions-architect/learner-profile.md`

## Diagnostic questions

1. A public API receives unpredictable spikes from hundreds of requests per second to tens of thousands per second. Each request triggers image processing that can take 20 to 90 seconds. Which compute and integration pattern would you choose, and why?
2. A company is rebuilding a batch-heavy monolith into services. One step must call a third-party API with strict rate limits, one step can run for up to 30 minutes, and the business wants visible workflow state for operators. Which AWS services fit best, and what tradeoffs matter most?
3. An internal trading support tool needs sub-second response times during market hours, uses custom native dependencies, and has a small platform team that wants to minimize operational toil. Where would you start on AWS, and what would make you change that choice?

## Learner responses and observations

- Strong signals: Solid first-pass reasoning on compute selection by workload pattern, cost profile, and operational overhead. Correctly used EventBridge for event fan-out, SQS for decoupled downstream work, and Step Functions for workflow-style processing such as fraud review. For a spiky image-processing API, correctly moved toward API Gateway plus async queueing and decoupled workers, and recognized that EC2 or other non-Lambda compute may be better when processing is long-running or may require specialized hardware such as GPUs. For a decomposed batch workflow, correctly selected Step Functions to provide explicit workflow state and identified EC2 or Fargate as better fits than Lambda for a 30-minute processing step. Suggested a token-bucket style approach as a way to think about enforcing a vendor rate limit. Showed good architectural restraint by preferring measured concurrency control when latency distribution indicates it is sufficient, instead of defaulting to extra machinery. On the final ordering scenario, recognized that ordered processing plus duplicate risk points toward a queue-centric design and that idempotency must live in application logic.
- Hesitations: Still needs sharper judgment on when a consumer should receive an EventBridge event directly versus through its own SQS queue, when Lambda is still viable despite high request volume, and how often exam answers should explicitly mention idempotency and failure-handling boundaries.
- Missing assumptions: Has not yet fully called out FIFO-specific design choices such as message groups and deduplication, dead-letter handling, or the distinction between workflow orchestration and choreography in broader event-driven systems.

## Misunderstandings to correct

- SQS and EventBridge are not interchangeable even though both can decouple producers and consumers.
- Step Functions is not just "workflow logic"; it is useful when the architecture needs explicit state transitions, retries, branching, timeouts, and operator-visible progress.
- Breaking up a batch-heavy monolith does not automatically imply moving to real-time stream processing; the right target could still be orchestrated asynchronous workflows with controlled throughput.
- Ordered customer-by-customer processing should usually start with SQS FIFO and message-group design, not just "a single worker," because one worker limits system throughput more than necessary.

## Action items

- Learner follow-up: Review SQS FIFO, message groups, deduplication, DLQs, and the exam-language difference between orchestration and choreography.
- Tutor follow-up: Revisit `SAP-D2-O1` with one short review scenario before or during `SAP-D2-O2`.

## Tracker updates

| Objective ID | Old status | New status | Confidence | Last reviewed | Next review | Evidence | Weak points | Next action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SAP-D2-O1 | not started | learning | 3/5 | 2026-03-29 | 2026-04-01 | Good first-pass compute and async tradeoff reasoning across EC2, Lambda, Fargate, SQS, EventBridge, and Step Functions. Could usually choose the right service family from scenario constraints. | Needs to state idempotency, FIFO/message-group design, DLQs, and direct-target vs queue-per-consumer decisions more explicitly. | Run a short review on failure modes and ordered event processing, then continue to `SAP-D2-O2`. |

## Next session recommendation

- Recommended objective(s): Brief review of `SAP-D2-O1`, then `SAP-D2-O2`.
- Why: The core judgment is developing well, and a short reinforcement pass should be enough before moving to storage and database tradeoffs.
