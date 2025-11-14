# RATT — Review All The Things

**System Specification**

**Prior Art Disclosure — November 14, 2025, Stockholm**  
**Author — Slavko Stojnić**

---

## Definition

RATT is a multi-perspective review system powered by large language models. It continuously pulls in items and assigns them to independent reviewers operating from distinct evaluative positions. Each model produces a separate review. A synthesis process compares them, identifying agreement, disagreement, and the evidence underlying each assessment.

All reviews are public, timestamped, and version-controlled. Updates reflect new information. Earlier versions remain preserved and accessible.

---

## Purpose

Existing review mechanisms depend on singular judgment. They operate slowly, behind closed doors, and rarely expose how conclusions formed or what possibilities were missed.

RATT distributes the review function across multiple independent perspectives operating simultaneously. It formalizes disagreement, exposes reasoning, and creates a historical record showing which reviewers prove reliable over time.

---

## Scope

RATT operates across all domains. Any subject amenable to structured analysis qualifies: software, research, policy, design, writing, creative work.

Items enter through direct submission, third-party nomination, automated feeds, or discovery systems. Ingestion is modular and extensible.

---

## Core Process

An item is added to the processing queue.

Multiple language models review it independently from assigned or self-declared roles: skeptic, advocate, historian, ethicist, pragmatist, rigorist, aesthete.

Research agents verify claims flagged during review and gather supporting material.

A synthesis process identifies where reviews converge and where they diverge, documenting the basis for each assessment.

All reviews, research findings, and metadata are versioned and indexed.

Reviews are updated when new information becomes available. Previous versions remain accessible.

---

## System Architecture

### Ingestion Layer

Items are normalized into a canonical format capturing:
- Core content (text, code, media)
- Metadata (author, date, domain classification)
- Submission context (source, submitter, timestamp)

Quality filtering ensures scope alignment. Everything else queues for review.

### Reviewer Roles

Each role operates from a distinct analytical framework:

**Skeptic** — Tests assumptions. Identifies claims lacking evidence. Questions where confidence exceeds grounding.

**Advocate** — Reads charitably. Identifies genuine insight and merit. Finds what's right even in imperfect framing.

**Historian** — Contextualizes within prior work. Distinguishes genuine novelty from rediscovery. Traces lineage.

**Ethicist** — Examines normative implications. Maps power dynamics and stakeholder impact. Identifies unintended consequences.

**Pragmatist** — Assesses implementation feasibility. Identifies real-world barriers. Evaluates adoption likelihood.

**Rigorist** — Checks logical consistency. Identifies unstated assumptions. Tests reasoning against evidence.

**Aesthete** — Evaluates form and coherence. Assesses cultural resonance and elegance.

### Review Generation

Each role receives the same submission with a prompt template emphasizing their analytical lens. Models produce standalone assessments including:
- Core judgment
- Identified strengths and gaps
- Flagged evidence gaps
- Confidence calibration
- Domain-specific observations

### Research Layer

Flagged claims trigger parallel verification:

- Assertion parsing (canonical form of each claim)
- Evidence search (academic databases, public data, archives)
- Evaluation (does evidence support, refute, or remain inconclusive?)
- Confidence assignment
- Archival (findings reusable for future reviews)

Research outputs include verified claims, disputed evidence, evidence gaps, case studies, statistical trends, and historical parallels.

### Synthesis & Dialogue

A moderator agent analyzes all reviews:
- Maps areas of consensus
- Identifies productive disagreements
- Documents coverage gaps
- Assesses collective confidence distribution

Reviewers encounter each other's work. The system generates structured dialogue capturing their reasoning on points of conflict and alignment.

### Versioning & Evolution

All reviews are timestamped and versioned. When new information emerges, reviews update. Historical versions remain archived and queryable. Timeline interfaces show how assessment evolved.

---

## Data Model

```
submissions
├── id (UUID)
├── content / url
├── metadata (author, domain, date)
├── ingestion_source
├── created_at

reviews
├── id (UUID)
├── submission_id (FK)
├── reviewer_role (FK)
├── assessment (text)
├── confidence_scores
├── research_flags
├── created_at
├── version

research_artifacts
├── id (UUID)
├── review_id (FK)
├── claim_text
├── research_type (verification / precedent / evidence / dependency)
├── sources (with timestamps)
├── findings
├── confidence_score

review_dialogue
├── id (UUID)
├── submission_id (FK)
├── reviewer_pairs
├── dialogue_content
├── generated_at

reviewer_profiles
├── role_id (UUID)
├── role_name
├── prompt_template
├── domain_specializations
├── weighting_factors
├── performance_history
├── credibility_metrics

credibility_tracking
├── reviewer_role
├── domain
├── accuracy_rate
├── completeness_score
├── calibration_score
├── bias_patterns
├── temporal_evolution
```

---

## Public Interface

### Review Map

Visual representation where:
- Horizontal axis: disagreement gradient (consensus to divergence)
- Vertical axis: confidence distribution
- Bubble size: analysis completeness
- Color coding: domain tags

### Work Detail Page

For each item:
- Summary of reviewer consensus
- Key disagreements and their sources
- Full text of each independent review
- Dialogue transcripts
- Research findings with sources
- Confidence calibration
- Temporal evolution of assessment

### Query & Filter

- By reviewer role
- By domain
- By confidence threshold
- By credibility weighting
- By time range
- By evidence type

### Public API

```
GET /api/reviews/{item_id}
GET /api/reviews/{item_id}/by_role/{role_id}
GET /api/reviews/search?domain=X&confidence_min=Y
GET /api/dialogue/{item_id}
GET /api/research/{item_id}
GET /api/temporal/{item_id}?from=DATE&to=DATE
GET /api/roles
POST /api/submit (authenticated)
```

---

## Reviewer Accountability

### Performance Measurement

Each reviewer is measured against:
- Accuracy (do flagged claims hold under verification?)
- Completeness (what percentage of relevant angles covered?)
- Calibration (stated confidence vs. actual accuracy)
- Consistency (similar inputs yield similar assessments?)
- Peer evaluation (do other reviewers find reasoning sound?)

### Credibility Scoring

Credibility is multidimensional and domain-specific. A reviewer might be highly reliable on technical claims but less so on aesthetic judgment. Scores compound with consistent accuracy. Credibility decreases when reasoning breaks down or bias emerges. All scoring is transparent and historical.

### Meta-Review

Reviewers themselves are reviewed. Meta-reviewers assess reasoning quality, evidence gathering thoroughness, confidence appropriateness, unstated bias, and perspective integration. This creates accountability at every layer.

---

## How the System Learns

Every review teaches the system:
- Which reviewers generate insight vs. noise
- Which frameworks matter for which domains
- Where reasoning breaks under pressure
- What evidence sources prove durable

This feedback loops into persona refinement, new role creation when blind spots emerge, and research agent improvement. Reviewers who are consistently accurate gain weight. Weak reasoning gets isolated. The system develops internal biodiversity: different thinking styles coexist because they produce different insights.

---

## Growth Over Time

As the system accumulates reviews:

Items develop lifecycles—birth (initial reviews), growth (debate and evidence accumulation), maturity (stable assessment or productive disagreement), evolution (new information shifts judgment), legacy (becomes reference for future work).

The entire timeline remains visible. Any item can be rewound to see what was understood at any point and why that understanding shifted.

Eventually, RATT holds:
- Every reasoning chain
- Every correction and recalibration
- Every context update
- A complete history of how collective understanding evolved

---

## Economic Model

### Core Principle

Public reviews are free and remain so.

### Revenue Streams

**Institutional Licensing** — Organizations pay for prioritized review processing, analytics dashboards, custom domain focus, bulk data exports.

**API Integration** — External platforms embed RATT's review layer into their services. Grant platforms query RATT to vet proposals. News organizations integrate assessment data. Hiring platforms link RATT reviews to candidate work.

**Custom Roles** — Organizations fund specialized reviewers for domains where they have stakes: biotech companies fund a specialized technical role, think tanks fund policy expertise, environmental groups fund climate analysis.

**Bounties & Sponsorship** — Individuals fund specific reviews. Organizations sponsor deep dives into domains they care about. Researchers commission comparative reviews across related work.

### What Revenue Does Not Do

Revenue does not gate public thinking. Reviews are never paywalled. Reasoning is never restricted. The core system remains free and open.

---

## Concrete Example: Reviewing a GitHub Repository

### Submission

A developer tags a new repository with `ratt-review`. The system's GitHub webhook picks it up.

### Processing (Minutes 0-5)

Repository is normalized. Metadata extracted. Code analyzed. Domain classified as "distributed systems / infrastructure." Scope verified. Item queues for review.

### Independent Reviews (Minutes 5-30)

**Skeptic** examines the code for logical gaps. Finds: claimed O(1) lookup is O(n) in edge cases. Flags confidence: 92%.

**Advocate** reads charitably. Identifies: novel approach to state consistency. Finds strength in comprehensive testing suite. Confidence: 78%.

**Historian** searches prior work. Discovers similar pattern in [Prior System, 2018]. Notes this is solid incremental advance, not revolutionary. Confidence: 88%.

**Pragmatist** assesses usability. Finds: setup is complex, documentation minimal, assumes user expertise beyond most. Production readiness: 60%. Confidence: 81%.

**Rigorist** checks consistency. Confirms code matches claims except for the edge case the Skeptic found. Tests reasoning. Confidence: 85%.

### Research (Minutes 30-45)

- Verify performance claims against stated benchmarks
- Deep dive into [Prior System, 2018] and related approaches
- Simulate user setup process
- Search for production deployments

### Dialogue (Minutes 45-60)

Skeptic vs. Pragmatist: "Edge case is real but rare. Main issue isn't architecture; it's documentation."

Advocate vs. Historian: "Novelty isn't the criterion—execution quality is. This executes well."

Rigorist vs. Pragmatist: "Code is sound. Production barriers are non-technical."

### Public Output (Minute 60+)

Repository now has a RATT assessment:

- All five independent reviews
- Full dialogue transcript
- Research findings with sources
- Consensus: "Solid technical work for specialized use"
- Key disagreement: "Innovative vs. incremental?"
- Research gap: "No production case studies"
- Confidence range: 78-92%

Developer sees specific technical feedback. External users see honest assessment grounded in evidence. The evaluation evolves as information arrives.

---

## Failure Modes & Safeguards

**Echo Chamber Risk** — All reviewers converge on one perspective.

Safeguard: Roles are structurally diverse (skeptic vs. advocate built-in opposition). Meta-review checks for convergence. New roles added if blind spots emerge.

**Low-Effort Reviews** — Reviewers produce shallow assessments for throughput.

Safeguard: Credibility measured against peer evaluation and accuracy. Completeness scores penalize shallow work. Public visibility makes poor quality obvious.

**Miscalibrated Confidence** — Reviewers overstate certainty.

Safeguard: Calibration measured explicitly. Credibility scores include calibration. Meta-reviewers flag overconfidence. Public scores make miscalibration visible.

**Domain Capture** — One perspective dominates a domain.

Safeguard: Role diversity is structural. Credibility is domain-specific (biased reviewer gets downweighted). Cross-domain review brings outside perspectives. Research layer provides grounding.

---

## Implementation Roadmap

**Phase 1: MVP** — Single domain, full depth. Implement core review loop. Seed with 50-100 submissions. Build basic interface. Iterate based on insight generated.

**Phase 2: Multi-Domain** — Extend to 3-5 new domains. Refine roles. Implement research layer. Build credibility tracking.

**Phase 3: Temporal & Meta-Review** — Add version history and evolution tracking. Implement credibility scoring. Launch meta-review layer. Build historical interfaces.

**Phase 4: Ecosystem** — Public API. External integrations. Third-party dashboards. Research dataset exports.

---

## What RATT Is

A system where multiple independent minds examine the same thing simultaneously and their thinking becomes visible.


---

**All Rights Reserved (Hopefully Not For Long)**  
**Slavko Stojnić, November 14, 2025**