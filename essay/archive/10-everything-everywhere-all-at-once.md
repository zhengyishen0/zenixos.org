---
date: 2026-03-24
---

# Everything, Everywhere, All at Once

Skills make Zenix a growing whole of parts. Mesh pushes it beyond — spreading those parts across devices while keeping them working as a whole.

## The Problem with "My Computer"

Today, your computing power lives in boxes. Your laptop has its CPU, its storage, its installed software. Your desktop has a different set. Your phone, another. Your home server with the GPU, another. Each is an island.

For a human user, this is annoying but manageable. You know which machine has which tool. You SSH into the server when you need GPU power.

For an AI agent, isolated machines are a fundamental constraint. An agent launched on your laptop can only use the skills installed on your laptop, only access the storage on your laptop, only run models your laptop can handle. Its capability is bounded by the device it happens to run on.

This is wrong. Capability should have no physical boundary.

## Mesh: The Organism Spreads

**Mesh** connects registered devices into a unified network. Auto-discovery finds devices on your local network. When devices are behind different networks, the system handles traversal automatically — punching through NATs, relaying through other nodes when direct connection isn't possible. Each device propagates its current address across the mesh, so every node maintains an up-to-date view without a central registry.

The system is most reliable with three or more nodes. For bootstrapping, you can opt into a shared Zenix-official node for orchestrating initial connections — centralization as convenience, not requirement.

Each device controls what it shares. You declare which skills to expose and which resources — RAM, CPU, GPU, storage — to make available. Other devices use these transparently.

## Declare What You Need

When an agent needs a skill, Mesh resolves it through a simple chain:

**Local first** — if the skill is installed on this device, use it. **Network** — if the skill is exposed by another device in the mesh, use it remotely. **Install from repo** — if a repository is specified and the skill isn't anywhere in the mesh, prompt to install.

This is influenced by Nix. We learned from Nix that declarative resolution works — you state what you need, the system figures out how to provide it.

But there's a deliberate departure. Nix's power comes from immutability — every package is a fixed derivation in a content-addressed store. Zenix's skills are explicitly mutable — they evolve through use, accumulate LEARNED.md entries, get refined over time. We get reproducibility through version control rather than immutable store paths. Different mechanism, similar safety net, but designed for living software rather than frozen packages.

What you state is what you get.

## Why This Works

Distributed computing across heterogeneous devices is an enormously hard problem — for general-purpose computing. AI agent workloads have properties that make it tractable.

Most agent operations are latency-tolerant. Code generation, document processing, search, analysis — these don't need millisecond response times. An extra 50ms of network latency is invisible in a task that takes 30 seconds of inference.

Most agent workflows are async-friendly. An agent working on a branch doesn't need real-time synchronization. It works, pushes, moves on. Watcher handles state change notifications asynchronously.

Skills are self-contained. A skill directory has everything needed — documentation, tools, learned knowledge. No hidden dependency on local state that would break remotely.

The system runs on universally available primitives: shell, filesystem, network sockets. These exist on every platform — Windows, macOS, Linux, Android.

## Resource Sharing

Mesh isn't just skill-sharing. Each device can expose compute resources as services. Run a powerful open-source LLM on your GPU desktop. Use it from your laptop. Access storage on your NAS. The physical location of resources becomes invisible.

The agent that uses a skill is still invoked by a specific device, even if the skill executes remotely. Decision-making stays local. Execution can be remote. This keeps the trust model simple: you trust your devices, Mesh lets them share.

## What's Still Hard

The networking and discovery layer is built on proven technology. But higher-level coordination has open questions.

What happens when a remote skill disappears mid-task? The agent needs a graceful degradation path, not a crash. When multiple agents request the same GPU simultaneously, who gets priority? The authentication and authorization story between nodes needs more work.

These are real challenges. The foundation is solid. The upper layers are being built. We'd rather be honest about the edges than pretend the picture is complete.

## Capability Without Boundary

An organism shouldn't stop at the edge of one machine. If a skill exists anywhere in your network, it should be available everywhere. If compute is available anywhere, it should be usable everywhere. The physical distribution of resources is an infrastructure concern, not an intelligence concern.

That's what an operating system should be in a world where intelligence is abundant and capability should flow freely.
