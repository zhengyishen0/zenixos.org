---
date: 2026-03-24
---

# Context Engineering Is an Operating System

We have many trendy concepts in the AI agent world. We used to have prompt engineering. Now we have context engineering. These are good concepts, but the problem is we don't always know what we're actually talking about — we just know the words make us feel smart.

## Prompt Engineering: You've Been Doing It Your Whole Life

Prompt engineering is knowing how to ask good questions, how to give clear instructions, and how to lead conversations through complications.

If you observe carefully, you'll find that any good leader, teacher, or communicator is naturally a good prompt engineer. That's what they do every day. They frame problems, guide thinking, and steer conversations toward useful outcomes. They've been prompt engineering **Anthropic Intelligence** their whole careers — directing human minds with words. Now they just reuse that skill on **Artificial Intelligence**.

Prompt engineering is local optimization. It makes a single interaction better.

## Context Engineering: This Is Where It Gets Hard

Context engineering is fundamentally different. It's not about how we talk to intelligence. It's about how we enable intelligence to operate.

Let's keep the human metaphor. How do we do context engineering for Anthropic Intelligence? If that question sounds strange, try rephrasing it: *how do we turn human beings into human resources?*

With tools (MS Office, AutoCAD). Instructions (PRDs, kanban boards). Iteration from feedback (daily standups, retrospectives). And access to institutional knowledge (wikis, Slack history, shared drives).

Context engineering is providing the right tool, the right internal instruction, and the right access to external information required for completing a specific task.

Here's the tricky part: the boundary of what tools, instructions, and access a task requires is impossible to fully predetermine before the task is complete. The scope is, essentially, everything. Any piece of context might turn out to be the critical one.

## The Scale of the Problem

Think about what it took to solve context engineering for humans.

We needed entire ecosystems of applications running on multiple operating systems across different devices. From WhatsApp to Slack to MS Office to AutoCAD. From mobile apps to web services. From laptops to phones to servers. Decades of hardware evolution. Decades of software evolution.

If it took all of that to make human beings productive in organizations, how can we expect to solve the context engineering problem for artificial intelligence with a RAG database and a chat window?

## The Assumption Underneath

There's an economic assumption that most people in AI haven't stated explicitly, but it explains everything:

**Intelligence is becoming abundant. Structure is scarce.**

Traditional computing assumed compute was expensive and data was structured. Build the schema first, optimize the queries, conserve processing power. That world made sense when intelligence was the bottleneck.

We're entering a different world. LLM inference is cheap and getting cheaper. The bottleneck has shifted. It's no longer "can the system think well enough?" It's "does the system have the right context to think about?"

If intelligence is abundant and context is the bottleneck, then the entire infrastructure question changes. You stop asking "how do we make AI smarter?" and start asking "how do we build the best possible environment for intelligence to operate in?"

That question doesn't lead you to a better prompt. Or a larger context window. Or a fancier retrieval pipeline.

It leads you to an operating system.

## AI Deserves Its Own OS

Just as Linux has a kernel, an OS layer, and applications, an agentic system has the exact same mapping:

- The **LLM** is the kernel — the raw intelligence that processes input and generates output
- The **agent framework** is the OS — managing sessions, resources, and coordination
- **Skills** are the applications — encapsulated capabilities the intelligence uses to accomplish work

This isn't a metaphor. It's an architectural decision. And it's the premise behind what we're building with Zenix.

![Diagram: two parallel stacks side by side. Left: traditional computing — Applications → OS → Kernel → Hardware. Right: agentic system — Skills → Agent Framework → LLM → Hardware. Dotted lines connect corresponding layers. The agentic stack uses purple to distinguish from the gray traditional stack.](post_01_parallel_stacks_dark.svg)

## What Comes Next

This is the first in a series of posts about the design and philosophy of Zenix. The series explores the nature of AI as an intelligence, the design philosophy behind each component, and how they compose into a living system.
