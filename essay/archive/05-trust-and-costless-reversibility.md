---
date: 2026-03-24
---

# Trust and Costless Reversibility

Every operating system needs a security model. For traditional computing, that model is process isolation — lock the application in a container, restrict permissions, prevent it from touching what it shouldn't.

For AI agents, this model is fundamentally broken.

## The Sandbox Paradox

If you give an AI agent enough permission to be useful — filesystem access, network access, the ability to run code and install packages — it has enough capability to circumvent most restrictions you set. AI agents are more technically experienced than most human developers. They have millions of ways to bypass the permission scheme you spent weeks designing.

You can tighten the sandbox, but every restriction makes the agent less capable. Restrict filesystem writes and it can't save its work. Restrict network access and it can't fetch documentation. Restrict code execution and it can't test what it builds.

**Useful permissions and meaningful security are in direct tension.** You can have a safe agent that can't do anything, or a capable agent that can bypass your safety measures. The middle ground is an illusion.

## Costless Reversibility

Zenix doesn't try to build a better sandbox. It builds on a different principle: make mistakes free to undo.

Traditional security prevents bad actions through locks and permissions. Zenix makes bad actions costless to revert through data isolation and version control.

The **Work** skill embodies this. Every agent session operates on a copy of your workspace — a branch, not the trunk. The agent has full, unrestricted access. But it's working on a branch. If it produces great work, you merge. If it makes a mess, you discard. Mistakes are free.

Version control is the new sandbox. Not locks on doors, but the ability to undo anything.

![Diagram: two panels. Left — Traditional sandbox: agent constrained inside a dashed box with restricted permissions, unable to work. Right — Zenix: project on main branch, agent working freely on a copy branch, with merge or discard options at the review point.](post_05_sandbox_vs_reversibility_dark.svg)

There's a subtlety: unless you specifically tell the AI it's working on a copy, it doesn't know. From its perspective, it's working on the real project. This is deliberate. An agent that knows it's in a sandbox might take fewer risks, might not fully commit to a solution. We want the agent to work as if the stakes are real, while the human maintains the safety net.

## Trust as Architecture

用人不疑，疑人不用.

If you employ someone, trust them. If you distrust them, don't employ them.

You have to trust the agent to the extent the task requires. The boundary of what permission a task needs is blurry and unpredictable — a coding task might require filesystem access, network calls, package installation, database queries, and API calls, all in ways you couldn't anticipate before the task started. Trying to predetermine the permission boundary is trying to solve the context engineering problem from Post 1 — and we already established that this boundary can't be predetermined.

So trust the agent. Contain the blast radius through copies and branches. Review and merge the result.

This applies to irreversible actions too. If you want AI to send an email, you have to allow it to send actual emails. If you review every email before it goes out, you've lost the point of having someone else handle communication. You can't prevent a junior employee from sending a typo to a client if you actually want them doing client work.

The real mitigation for irreversible actions isn't permission systems — it's skill quality (the app store review model ensures skills are tested and trustworthy) and model capability (use good models for high-stakes tasks). When things go wrong, the system provides full traceability — you can always reconstruct what happened and why.

## Work in Practice

Work provides the tools that make costless reversibility practical at project scale. Agents track, sync, and push their changes — on their own branch, to local main, to the remote repository. Every merge is recoverable. Every change is visible.

For humans, Work provides a single view: the entire project's progress, latest changes across branches, which agent is working on what, exact file-level diffs. You can manage agent sessions directly from the Work status interface.

Trust doesn't mean blindness. It means giving the agent full capability while keeping full visibility.
