---
date: 2026-03-24
---

# Everything, Everywhere, All at Once

## The Constraint That Doesn't Need to Exist

Your computing power lives in boxes. Your laptop has its processor, its storage, its installed capabilities. Your desktop has a different set. Your phone, another. Your home server with the GPU, another. Each is an island.

For a human user, this is annoying but manageable. You know which machine has which tool. You SSH into the server when you need GPU power. You copy files between devices. The friction is real but navigable, because you carry a mental map of what's where.

For AI, isolated machines are a fundamental constraint. An agent launched on your laptop can only use the capabilities installed on your laptop, only access the storage on your laptop, only run models your laptop can handle. It has no mental map of your other devices. Its world ends at the edge of the machine it happens to start on.

Capability should have no physical boundary.

## Declarative, Not Imperative

There are two ways to get what you need from a system.

The imperative way: step-by-step commands. Go to this machine. Install this package. Configure this dependency. Run this service. Each step depends on the previous step's result. If any step fails, you troubleshoot from that point. The process is stateful — the system accumulates state with each command, and the order matters.

The declarative way: describe what you need. "I need a capability that can process images using a GPU." The system figures out where that capability exists, how to access it, and provides it. No steps. No order dependency. No accumulated state.

This distinction should sound familiar. It's the same principle from Post 7 — stateless interfaces over stateful internals — extended from a single machine to the entire network. And it matches AI's nature for the same reasons.

Declarative is stateless. No step depends on the previous step. The agent describes the desired state and the system resolves it. If the resolution fails, the agent can re-declare without worrying about what state was left behind by a partial attempt.

Declarative is text-native. The agent describes what it needs in words — the same way it does everything else. "I need image processing with GPU access" is text in, capability out. The same dimension AI already operates in.

NixOS understood this for human computing. Instead of imperatively installing packages and mutating system state (`brew install`, `apt-get`, `pip install` — each one changing the system in ways that depend on what was installed before), Nix lets you declare the entire system configuration in a text file. The system materializes it. Reproducible, stateless, text-native.

For AI, declarative capability resolution isn't just a convenience — it's the natural mode. The agent already works by describing what it wants and letting the system figure out how to provide it. Extending this from "describe what you want the model to generate" to "describe what capabilities you need the system to provide" is a continuation of the same principle, not a new one.

## The Parts Work as One

When declarative resolution works across devices, something qualitative changes. The agent doesn't think about machines. It doesn't know that the image processing happened on your desktop's GPU while the text analysis happened locally on your laptop. It described what it needed. The system provided.

Each device controls what it shares — which capabilities to expose, which resources to make available. The agent on one device transparently uses capabilities and compute from another. A powerful open-source model running on your GPU server is accessible from your phone. Storage on your NAS is available to an agent running anywhere. The physical distribution of resources becomes invisible.

Everything available. Everywhere accessible. All at once.

From the agent's perspective, there is no network. There are no separate machines. There is only the set of capabilities it can describe and use. The infrastructure resolves the rest.

## Why AI Makes This Tractable

Distributed computing across heterogeneous devices is an enormously hard problem for general-purpose computing. AI agent workloads have properties that make it tractable.

Most agent operations are latency-tolerant. Code generation, document processing, analysis — an extra 50ms of network latency is invisible in a task that takes 30 seconds of inference.

Most agent workflows are async-friendly. An agent working on a branch doesn't need real-time synchronization. It works, pushes, moves on.

Capabilities are self-contained. A capability directory has everything needed — documentation, tools, field notes. No hidden dependency on local state that would break when accessed remotely.

## What's Still Hard

The foundation is tractable. But higher-level coordination has open questions.

What happens when a remote capability disappears mid-task? The agent needs graceful degradation, not a crash. When multiple agents request the same GPU simultaneously, who gets priority? Authentication and authorization between devices needs more work.

These are real challenges. The foundation is solid. The upper layers are being built. We'd rather be honest about the edges than pretend the picture is complete.

## Why the Machine Boundary Is a Human Assumption

Every operating system ever built has had edges. Your laptop runs its OS. Your phone runs its OS. Your server runs its OS. Each is a self-contained world with clear boundaries.

This makes sense for humans. You have a physical location. You're at your laptop, or you're at your desktop, or you're on your phone. Your body is in one place, so your computing environment has a center — the machine in front of you. The OS boundary maps to your physical boundary.

AI has no physical location. It exists wherever context exists. An agent doesn't sit at a machine the way a human does. It's instantiated in a context window that could be assembled from capabilities on any device, from memory stored anywhere, from tools running on any machine in the network. The agent's "location" is its context, not a device.

An operating system designed for a being with no physical location shouldn't have physical boundaries. The machine boundary — this device's capabilities vs. that device's capabilities — is an assumption that carried over from human computing because no one questioned it. Text-native, stateless, declarative — every principle we've established is indifferent to which machine it runs on. The principles don't have edges. The OS shouldn't either.

Everything, everywhere, all at once. Not as aspiration, but as the natural consequence of building for a being that was never in one place to begin with.
