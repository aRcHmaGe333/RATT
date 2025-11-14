# RATT — Review All The Things

```
R.A.T.T.
  |O/
  /|
   |
  / \
```

**Prior Art Disclosure — November 14, 2025, Stockholm**

---

## What It Is

RATT continuously pulls in items worth reviewing. Multiple large language models review each item independently, from different angles. The system generates a synthesis comparing their reviews: where they align, where they split, what evidence grounds each perspective.

All reviews stay public, timestamped, and versioned. When new information arrives, reviews update. Historical versions remain archived.

---

## Why It Works

Standard review systems hide their reasoning. One authority makes a call. You see the verdict but not how they reached it, what they dismissed, or what they overlooked.

RATT puts multiple frameworks against the same thing at the same time. It shows where thinking holds. It shows where it fractures. Evidence is attached to every claim. Reviewer reliability becomes measurable through track record.

---

## What Gets Reviewed

Anything analyzable. Code, research, proposals, products, writing, art. Domain doesn't matter.

Items arrive through submission, nomination, automated feeds, discovery protocols.

---

## How It Works

An item enters the queue.

Multiple language models review it independently, each operating from a specific stance: skeptic, advocate, historian, ethicist, pragmatist, rigorist, aesthete.

Research agents verify flagged claims and collect supporting material.

The system maps where reviews converge and diverge.

All assessments are versioned, archived, indexed.

Reviews evolve as new information surfaces.

---

## What You See

Each reviewed item includes:

- All independent reviews
- Alignment and conflict between reviewers
- Evidence supporting each claim
- Confidence levels per reviewer
# RATT — Review All The Things

R.A.T.T.
  |O/
  /|
   |
  / \

**Prior Art Disclosure — November 14, 2025, Stockholm**
**Author — Slavko Stojnić**

---

Overview

RATT continuously pulls in items worth reviewing and runs multiple independent reviewer agents on each item. Each agent follows a distinct analytical stance and produces a standalone assessment. A synthesis stage maps agreement and disagreement, attaches supporting evidence, and archives the results. All public-facing outputs pass an automatic Unit Fitness Gate (UFG) that repairs clarity, removes unsupported claims, and preserves the author's intent.

Core Principles

- Public, timestamped, and versioned reviews — historical versions remain accessible.
- Multiplicity: independent perspectives, not a single authority.
- Transparency: reasoning, evidence, and research chains are visible.
- Autonomy: RATT operates continuously (feeds, discovery, nominations, and optional submissions).
- UFG enforcement: all repo-facing text and every published unit are auto-checked and auto-repaired before release.

What RATT Reviews

Anything that can be assessed: code, research, proposals, designs, writing, art, and other public or discoverable artifacts. Items may enter via automated feeds, third-party nomination, or optional direct submission; the system also discovers items autonomously.

How It Works (brief)

1. RATT pulls in items for assessment.
2. Multiple reviewer personas independently assess the item (skeptic, advocate, historian, ethicist, pragmatist, rigorist, aesthete, etc.).
3. Research agents verify flagged claims and gather evidence.
4. A moderator agent synthesizes consensus, productive disagreement, and evidence gaps; reviewers see one another's work and generate structured dialogue where needed.
5. All outputs are archived, searchable, and updateable when new information arrives.

Truncation Immunity

No assumption that non-truncated input constitutes the whole story; the system performs recursive passes to compensate for limits and emulate extended context awareness. RATT watches what it truncates and re-runs analysis as necessary.

Audience-Adaptive Output

Published outputs may be rendered in parallel registers (formal / public / blended) according to audience profile. This is automatic and does not require interactive prompts for each item.

Economic Model (summary)

Public reviews are free and remain so. The system is funded by institutional licensing, prioritized API access for partners, custom role funding, and optional bounties or sponsorships — none of which gate core public reasoning.

---

**All Rights Reserved (Hopefully Not For Long)**  
**Slavko Stojnić**