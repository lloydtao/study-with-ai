# Research: How to Study for the AWS Solutions Architect Professional Exam

## Research question

As of 2026-03-28, what exists in this codebase and in current internet-accessible sources about how to study for the AWS Certified Solutions Architect - Professional (SAP-C02) exam?

## Summary of findings

- The current codebase does not contain application code, exam logic, or existing AWS certification notes. Today it is a lightweight notes repository with root metadata files and an otherwise empty `thoughts/research/` directory prior to this document.
- The repository's only explicit purpose statement is in `README.md`, which describes the project as "Personal study notes using LLMs as a tutor."
- AWS currently exposes the main study path for this exam through three connected official entry points:
  - the certification overview page for AWS Certified Solutions Architect - Professional
  - the SAP-C02 exam guide and its companion scope pages
  - the Solutions Architect learning page and downloadable ramp-up guide
- The certification overview page currently describes a four-part preparation flow: understand the exam with exam-style questions and the exam guide, refresh AWS knowledge with courses and hands-on products, review domains with questions and instructor-led prep content, and assess readiness with the official practice exam.
- The SAP-C02 exam guide currently defines the role as an advanced solutions architect exam and frames preparation around four domains:
  - Design Solutions for Organizational Complexity: 26%
  - Design for New Solutions: 29%
  - Continuous Improvement for Existing Solutions: 25%
  - Accelerate Workload Migration and Modernization: 20%
- AWS's broader study corpus for this exam currently spans:
  - AWS Well-Architected
  - AWS Architecture Center
  - AWS Prescriptive Guidance for migration and modernization
  - role-based training via Skill Builder and the Solutions Architect ramp-up guide
- The main unresolved gap is that the AWS Skill Builder exam-prep pages are JavaScript-gated in text-only browsing, so the exact current contents of the linked four-step plan, official practice question set, and official practice exam were not directly inspectable here.

## Detailed findings by component

### 1. Repository root metadata

**Where it lives**

- `README.md`
- `.gitignore`
- `LICENSE`

**What exists today**

- `README.md` is the only tracked file that describes repository intent. It identifies the repo as `study-with-ai` and says it is for personal study notes using LLMs as a tutor.
- `.gitignore` contains a generic JavaScript and web-project ignore set, including entries for `node_modules/`, `.next`, `.nuxt`, `dist`, `coverage`, `.cache`, and other frontend or build artifacts.
- `LICENSE` is an MIT license.

**How these pieces interact**

- `README.md` establishes the repo as a notes workspace rather than an application codebase.
- `.gitignore` suggests the repo may be expected to coexist with JavaScript or static-site tooling at some point, but there are no tracked source files, config files, or build outputs present today that implement such a workflow.
- `LICENSE` provides the legal wrapper for the repository contents.

**Relevant pattern elsewhere in the codebase**

- The tracked file set is intentionally minimal. There are no source directories, package manifests, infrastructure templates, or existing domain-specific notes besides the newly created research note location under `thoughts/`.

### 2. Research workspace

**Where it lives**

- `thoughts/research/`

**What exists today**

- The `thoughts/` directory exists and contains a `research/` subdirectory.
- Before this document was created, `thoughts/research/` contained no tracked files.

**How it interacts with the rest of the repo**

- `thoughts/research/` is the only existing in-repo location clearly intended to hold structured research artifacts.
- In practice, that makes it the local sink for topic research, while the root files describe the repository at a high level.

**Relevant pattern elsewhere in the codebase**

- There is no alternative notes structure, knowledge base, or study taxonomy elsewhere in the tracked repository today.

### 3. AWS certification overview page

**Where it lives**

- https://aws.amazon.com/certification/certified-solutions-architect-professional/

**What exists today**

- AWS currently describes this credential as a professional-level certification for showcasing advanced knowledge in solving complex problems, optimizing security, cost, and performance, and automating manual processes.
- The page currently lists:
  - exam duration: 180 minutes
  - exam format: 75 questions, either multiple choice or multiple response
  - cost: 300 USD
  - delivery: Pearson VUE testing center or online proctored
  - languages: English, Japanese, Korean, Portuguese (Brazil), Simplified Chinese, and Spanish (Latin America)
- AWS currently presents a four-step preparation flow:
  - get to know the exam with exam-style questions and the exam guide
  - refresh AWS knowledge and skills with digital courses, AWS Builder Labs, AWS Cloud Quest, and AWS Jam
  - review the scope of the exam by domain, with questions, flashcards, instructor walkthroughs, and continued hands-on practice
  - assess readiness with the AWS Certification Official Practice Exam
- The same page states that the recommended prior experience is two or more years using AWS services to design and implement cloud solutions.

**How it interacts with other components**

- This page is the public entry point into the rest of the AWS study system.
- It links outward to:
  - the SAP-C02 exam guide
  - the AWS service short-name list used in the exam
  - Skill Builder's four-step exam prep plan
  - official practice materials

**Relevant pattern elsewhere**

- The overview is outcome-oriented and high level, while the detailed content boundaries live in the exam guide and companion documentation pages.

### 4. SAP-C02 exam guide and companion scope pages

**Where they live**

- https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/solutions-architect-professional-02.html
- https://d1.awsstatic.com/training-and-certification/docs-sa-pro/AWS-Certified-Solutions-Architect-Professional_Exam-Guide_C02.pdf
- https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/sap-02-in-scope-services.html
- https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/sap-service-mentions.html

**What exists today**

- The SAP-C02 exam guide states that the exam is intended for individuals performing a solutions architect role.
- It says the exam validates advanced technical skills and experience in designing optimized AWS solutions based on the AWS Well-Architected Framework.
- The guide frames the role around four major task areas:
  - design for organizational complexity
  - design for new solutions
  - continuously improve existing solutions
  - accelerate workload migration and modernization
- The exam guide currently defines the domain weighting as:
  - Domain 1: Design Solutions for Organizational Complexity, 26%
  - Domain 2: Design for New Solutions, 29%
  - Domain 3: Continuous Improvement for Existing Solutions, 25%
  - Domain 4: Accelerate Workload Migration and Modernization, 20%
- The PDF version currently clarifies the exam structure as 65 scored questions plus 10 unscored questions, matching the public overview's 75-question total.
- The in-scope services page currently shows breadth across analytics, application integration, compute, containers, database, management and governance, migration and transfer, networking and content delivery, security, identity and compliance, and storage, among other categories.
- The companion "Mentions of AWS Services on the Exam" page explains that AWS now uses official short names for many services in the exam and exposes the list through the exam Help feature.

**How they interact with other components**

- The exam guide provides the canonical content map for what the certification overview calls "the scope of the exam."
- The in-scope services page and service-name page narrow the operational study surface by showing the service families and naming conventions that map into the exam domains.
- These pages form the boundary layer between generic AWS training and exam-specific preparation.

**Relevant pattern elsewhere**

- The exam guide emphasizes both architecture breadth and migration/modernization depth. That same emphasis reappears in the AWS Architecture Center, Well-Architected Framework, and Prescriptive Guidance resources linked elsewhere in AWS's training ecosystem.

### 5. Solutions Architect learning page and ramp-up guide

**Where they live**

- https://aws.amazon.com/training/learn-about/architect/
- https://d1.awsstatic.com/training-and-certification/ramp-up_guides/Ramp-Up_Guide_Architect.pdf

**What exists today**

- AWS's Solutions Architect learning page currently positions itself as a role-based learning starting point built by AWS experts.
- It links to a Solutions Architect Learning Plan in Skill Builder and states that the plan offers a suggested set of digital courses, can be taken at the learner's own pace, and is meant to reduce guesswork around course ordering.
- The same learning page points readers to the downloadable Solutions Architect Ramp-Up Guide for a broader catalog of learning materials including digital courses, blogs, whitepapers, and other resources.
- The current ramp-up guide contains both foundational and advanced material. Its later sections explicitly place professional-level prep near the end of the sequence and currently list:
  - `Advanced Architecting on AWS` as instructor-led training
  - `Exam Readiness: AWS Certified Solutions Architect - Professional` as exam prep
  - `AWS Power Hour: Architecting - Professional (Exam Prep)` as an on-demand stream
  - `AWS Cloud Quest: Solutions Architect` as game-based learning
  - additional resources such as AWS Well-Architected, the Shared Responsibility Model, AWS Architecture Center, Well-Architected Labs, sample CloudFormation templates, and AWS Elastic Disaster Recovery

**How they interact with other components**

- The learning page is the role-based entry point.
- The ramp-up guide expands that entry point into a sequenced catalog across courses, labs, game-based learning, and exam-specific prep.
- The ramp-up guide explicitly routes learners back into the deeper technical corpus:
  - Well-Architected
  - Architecture Center
  - security guidance
  - disaster recovery and infrastructure-as-code examples

**Relevant pattern elsewhere**

- AWS organizes study content in layers:
  - broad role-based onboarding on the learning page
  - a long-form curated list in the ramp-up guide
  - exam-specific boundaries in the SAP-C02 guide
  - domain-deep references in architecture and prescriptive guidance portals

### 6. Architecture and migration reference corpus

**Where it lives**

- AWS Architecture Center: https://aws.amazon.com/architecture/
- AWS Well-Architected Framework: https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html
- AWS Prescriptive Guidance: https://aws.amazon.com/prescriptive-guidance/
- Large migration strategies: https://docs.aws.amazon.com/prescriptive-guidance/latest/large-migration-guide/migration-strategies.html

**What exists today**

- The AWS Architecture Center currently positions itself as the hub for reference architecture examples and diagrams.
- It highlights AWS Well-Architected and decision guides as starting points for architects.
- The Well-Architected Framework currently defines six pillars:
  - operational excellence
  - security
  - reliability
  - performance efficiency
  - cost optimization
  - sustainability
- AWS Prescriptive Guidance currently describes itself as resources from AWS technology experts to accelerate cloud adoption and modernization.
- The large migration strategy guide currently documents the seven migration strategies, the "7 Rs":
  - retire
  - retain
  - rehost
  - relocate
  - repurchase
  - replatform
  - refactor or re-architect

**How they interact with other components**

- This corpus supplies the technical reference layer underneath the exam guide domains.
- Well-Architected directly matches the exam guide's framing around optimized solutions.
- Prescriptive Guidance maps especially closely to Domain 4, which covers workload migration and modernization.
- The Architecture Center gives decision guides and reference architectures that support design tradeoff reasoning across domains 1 through 3.

**Relevant pattern elsewhere**

- The same themes repeat across AWS resources:
  - architectural tradeoffs
  - resilience and cost/performance balance
  - migration strategy selection
  - service selection at enterprise scale
- The repetition suggests AWS expects preparation to combine exam-specific study with broader reference reading and hands-on architecting materials.

## Key file references

### Local codebase references

- `README.md`
- `.gitignore`
- `LICENSE`
- `thoughts/research/2026-03-28-1545-aws-solutions-architect-professional-exam-study.md`

### External references consulted

- AWS Certified Solutions Architect - Professional: https://aws.amazon.com/certification/certified-solutions-architect-professional/
- SAP-C02 exam guide landing page: https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/solutions-architect-professional-02.html
- SAP-C02 exam guide PDF: https://d1.awsstatic.com/training-and-certification/docs-sa-pro/AWS-Certified-Solutions-Architect-Professional_Exam-Guide_C02.pdf
- In-scope AWS services and features: https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/sap-02-in-scope-services.html
- Mentions of AWS services on the exam: https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-professional-02/sap-service-mentions.html
- Solutions Architect learning page: https://aws.amazon.com/training/learn-about/architect/
- AWS Ramp-Up Guide: Solutions Architect: https://d1.awsstatic.com/training-and-certification/ramp-up_guides/Ramp-Up_Guide_Architect.pdf
- AWS Architecture Center: https://aws.amazon.com/architecture/
- AWS Well-Architected Framework pillars: https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html
- AWS Prescriptive Guidance: https://aws.amazon.com/prescriptive-guidance/
- About the migration strategies: https://docs.aws.amazon.com/prescriptive-guidance/latest/large-migration-guide/migration-strategies.html

## Any open questions that need more investigation

- The certification overview page links to a Skill Builder four-step exam prep plan, an official practice question set, and an official practice exam. Those destination pages were JavaScript-gated in this environment, so the exact current lesson inventory, exercise count, and access requirements behind those links remain unverified from direct page contents.
- No existing local notes or code paths in this repository currently track this exam topic, so there is no in-repo study workflow, taxonomy, or prior research history to compare against.
