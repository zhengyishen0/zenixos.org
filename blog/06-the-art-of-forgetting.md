---
date: 2026-03-24
---

# The Art of Forgetting

One of the biggest pain points in working with AI is what happens to all those conversations. Context switch between sessions. Context pollution within a session. Context compaction when the window fills up. In the end, we don't care about the LLM model itself — we care about the conversations we've had with it. But with the current architecture of LLMs and coding agents, we lose those conversations every day.

## The Sophisticated Solutions That Don't Work

People have built sophisticated solutions. RAG pipelines. Multiple layers of embeddings. Vector databases with hybrid search. NLP-powered summarization chains.

These solutions share a common assumption: the way to help AI remember is to pre-process, structure, and index information so it can be retrieved precisely.

But if there's one lesson from the success of Claude Code, it's that simplicity wins. Claude Code uses simple grep and beats codebase indexing. Not because grep is a better algorithm — it's worse by every computer science metric. But it's simple enough that the AI uses it correctly almost every time, while complex systems introduce enough failure modes that the net result is worse.

Memory works the same way.

## Search, Don't Remember

How do you handle a messy SQL database? You don't try to clean it up. You don't reorganize the tables. You write better queries.

Conversation history is messy by nature. Full of tangents, corrections, half-formed ideas, context-specific references. No amount of preprocessing will make it clean. So don't try. Just search.

This is a deliberate tradeoff. Accept noise and inefficiency in exchange for flexibility, adaptability, and zero schema friction. Don't decide in advance what's important. Don't maintain an embedding index that drifts from actual content. Just ask the right questions at the right time.

## The Cold-Start Problem

Search is different from querying a database. Search is about exploring the unknown. And for a stateless intelligence — which has no persistent intuition about what's in its own history — exploring the unknown is hard.

A human searching their email has fuzzy memory to guide them. "I remember discussing this in March, the subject mentioned budgets." An LLM has none of this. Every search starts cold.

This is why the **Memory** skill provides three layers of support:

**Memory hints.** The system shows the AI relevant keywords and topic markers so it knows what exists in the searchable history. A table of contents before searching the library.

**Query refinement.** When initial results miss, the system helps reformulate — different keywords, different time ranges, different session scopes. Iterative search, the same way you refine a Google query when the first result misses.

**Cross-framework search.** Memory works across all coding agent frameworks and sessions. The search space is unified regardless of where the conversation happened.

Don't make the data smarter. Make the queries smarter. The data is a messy, append-only log. The intelligence is in how we search it.

## Attention Is All That Matters

The paper that started all of generative AI says it in the title: "Attention Is All You Need."

True in a deeper sense than the authors may have intended. Even as context windows grow — 100K tokens, 200K, a million — it's always best practice to keep only what matters in the active session. More context doesn't mean better performance. The *right* context means better performance.

Attention is not about how much you can hold. It's about what you choose to hold.

This is why **forgetting is as important as remembering**. A memory system that loads everything into the context window is actively harmful — it dilutes attention with noise, pushing out the signal that actually helps. Good memory is selective memory. Search finds candidates. Attention selects what matters. Everything else stays in the log, available but not active.

## Memory 2.0: Active Context Management

Memory 1.0 is read-only search. The agent searches history, retrieves what's relevant, uses it. The source of truth — the full chat logs — is never modified.

Memory 2.0 extends this with a critical capability: the agent can manipulate its own working memory.

The agent can summarize verbose exchanges into compact notes. Tag important decisions for easy retrieval. Prune context that's no longer relevant. Create structured encapsulations — cognitive compression that preserves meaning while reducing token cost.

The distinction matters: the agent edits its working memory (what's in context), not the source of truth (the full chat logs). Even if the agent makes bad decisions about what to keep, recovery is always possible by re-searching the raw logs.

Agents run much longer before needing context compaction. They produce better output because context is more relevant. They use fewer tokens because they're not carrying dead weight. And because an agent is essentially a runtime of its memory, managing its own memory means it can use itself as a service — reducing the need for sub-agents in many scenarios.

## Why Context Beats Orchestration

This last point deserves emphasis. The industry is converging on "AI teams" — multiple specialized agents coordinated by an orchestrator. The assumption is that complex tasks need multiple agents with different roles.

We think the premise is wrong.

Different agents are just different initial prompts for the same runtime. If you're using the same model and framework, Agent A with "you are a frontend developer" and Agent B with "you are a backend developer" are not two different intelligences. They're two different contexts. The "team" is an illusion — you've split one context into two smaller, less informed fragments and now you need an orchestrator to stitch them back together.

Every reason people reach for multi-agent reduces to a context problem. The task is too complex? That's a context management problem — an agent with good working memory handles far more complexity than one drowning in raw history. Need parallelism? That's independent work on separate branches, not coordination. Need specialization? That's loading a different skill, not maintaining a separate agent. Need cheaper execution? One agent with good context that gets it right in one pass costs less than three agents with bad context that need orchestration and error correction. Price per outcome, not price per token.

Instead of building orchestration, we invest in making single-agent context management so good that orchestration becomes unnecessary. Memory 2.0 is the core of that investment. The bet: one well-equipped agent with good context beats a team of poorly-equipped agents with an orchestrator.

## The Messy Truth

Memory 2.0 will reduce the need for detailed search in many cases. But it won't eliminate messiness. Conversations are messy by nature. And with more efficient memory, agents will have longer sessions, generating more history. The challenge doesn't shrink — it shifts.

The answer remains the same: search over structure. Better queries over cleaner data. Attention over accumulation.
