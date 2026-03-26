---
date: 2026-03-24
---

# Living Software

## The Four Properties

Before LLMs, only one thing in the world had all four of these properties simultaneously:

A **tool** that executes actions. A **manual** that teaches when and how to use it. **Accumulated experience** from actual use in the field. And the **ability to refine itself** based on what's learned.

That thing was a human employee.

A person with job training, a job description, on-the-job experience, and the ability to improve their own processes. The combination of these four properties is what makes an employee more valuable over time — not just functional, but developing.

Now imagine software with the same four properties. A capability that comes with documentation teaching AI how to use it. That accumulates field notes from every use — edge cases, workarounds, patterns. And that can modify its own implementation based on what's been learned.

This is what we mean by living software. Not because it's alive in any biological sense. Because it develops. It gets better through use, not just through human updates.

## Why Simplicity Is the Starting Point

The biggest progress in agentic intelligence has never come from sophisticated technology. It has come from simplicity grounded in a profound understanding of how intelligence works.

"Let's think step by step." Five words that unlocked chain-of-thought reasoning. Simple grep that beats codebase indexing. Markdown files that outperform complex configuration frameworks.

The pattern: the solution that wins is never the most sophisticated. It's the one simple enough for AI to use reliably every time. Simplicity isn't the ceiling. It's the starting point that actually works. Complexity can be earned later, through experience — not pre-engineered in advance.

Living software follows this pattern. On disk, it's just files in a directory. A markdown manual. Shell scripts. A field notebook. Nothing that requires a service registry, dependency injection, or configuration framework. Just files, conventions, and the filesystem.

The simplicity is the point. AI reads files reliably. It runs commands reliably. It writes to files reliably. Build on what works.

## How Living Software Learns

Every capability starts with its manual — the official documentation. What it does, how to use it, what to expect. This is the theory.

But living software also accumulates a second layer: field notes. When an agent uses a capability and encounters something worth remembering — an edge case, a workaround, a pattern that worked well, a mistake to avoid — it appends to the field notes.

The manual is the theory. The field notes are the practice.

When the next agent loads the capability, it reads both. The new hire gets the onboarding docs *and* the tips from the veteran.

## Three Layers of Evolution

Over time, living software evolves through three layers:

**Layer 1: Knowledge accumulation.** The field notes grow with each use. Edge cases documented. Workarounds noted. Patterns emerging. Raw experience, unstructured and append-only.

**Layer 2: Pattern crystallization.** Repeated patterns become visible. "Every time I use this for X, I end up doing Y first." These get extracted into reusable templates or scripts. Raw experience promoted to structured capability.

**Layer 3: Tool refinement.** When the field notes keep recording "this command fails on edge case X and the workaround is Y," eventually the tool itself gets patched to handle X directly. The software contains its own source code — it's just files in a directory — so modification is natural.

Here's what Layer 3 looks like in practice. A web-fetching tool originally returns raw HTML. The field notes accumulate entries across dozens of sessions: "Documentation sites include navigation bars, footers, and cookie banners that waste context tokens. Workaround: pipe the output through a text extraction step." Eventually, the tool itself is patched to accept a flag that strips non-content elements before returning. The workaround dissolved into the tool. The software absorbed what its users kept teaching it.

## Pruning: The Immune System

Field notes can accumulate noise. Outdated advice. Workarounds for bugs that were already fixed. Patterns that no longer apply. Edge cases patched in Layer 3. Noisy field notes are worse than no field notes — they waste the agent's limited attention on outdated guidance.

Living software needs pruning. Periodic retrospectives where an agent reviews accumulated knowledge and proposes what to keep, promote, or archive. This is the immune system of the ecosystem. Without it, accumulated wisdom degrades into accumulated confusion.

## Quality as Integrity

If living software is what autonomous agents depend on, quality is an existential concern. An unreviewed or unreliable capability used by an unsupervised agent is categorically more dangerous than a bad package used by a human developer. The human spots the problem. The agent trusts the documentation and acts.

This is why the right model is curated review, not open-source free-for-all. When your users are autonomous agents, quality control isn't a nice-to-have. It's system integrity.

## Curation, Not Accumulation

Every capability an agent has access to is a decision it might have to make — "should I use this?" That decision costs attention. A system with fifty capabilities where the agent hesitates between them is worse than a system with eight capabilities that compose cleanly.

This is the UNIX lesson: a small number of composable primitives beats a large number of specialized tools. `ls`, `cat`, `grep`, `pipe` — each one simple, together unlimited. The power is in the composition, and composition works best with fewer, better parts.

Core capabilities must be curated the way organs are evolved. Each must justify its existence not just by what it adds, but against the complexity it introduces. The discipline is in deleting more than you create. Users can extend the system freely. But the core remains selective, because a confused agent is worse than a limited one.

## Why "Living," Not "Smart"

A smart tool does clever things. A living tool gets better through use. The distinction matters because it changes what you optimize for. Smart tools optimize for capability at design time. Living tools optimize for learning rate over time.

Software that evolves through use by AI, not just through human updates. That's the primitive the operating system is built on.
