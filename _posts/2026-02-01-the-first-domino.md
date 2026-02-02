---
layout: post
title: "The First Domino: Why The ONE Thing Matters More Than Ever in the Age of Agentic AI"
date: 2026-02-01
---

Three weeks ago, I let Claude Code refactor a validation module in our codebase. I gave it what I thought was a clear spec: "Consolidate validation logic across these four files." I grabbed coffee, answered a few Slack messages, and returned to find 47 files changed, a broken build, and a Git history that looked like a crime scene.

The AI hadn't done anything wrong, technically. It had found "validation logic" I'd forgotten about—legacy code from a feature we'd deprecated two years ago. It dutifully consolidated everything, including code paths that should have stayed dead. Two hours of debugging later, I had a painful realization: **the AI didn't know when to stop. That was my job.**

After 13 years building distributed systems at Amazon, I've developed strong instincts for failure modes. I can smell a race condition before it manifests. But AI-augmented development has exposed a gap in my mental model—one that a book I'd read years ago, and mostly dismissed, suddenly made visceral.

Gary Keller's "The ONE Thing" argues that extraordinary results come from narrowing focus, not expanding it. The core question is deceptively simple: *What's the ONE Thing I can do such that by doing it everything else will be easier or unnecessary?*

When I first read it, I filed it under "productivity self-help"—useful for to-do lists, but irrelevant to systems engineering. I was wrong. In the age of Agentic AI, Keller's framework isn't just relevant. It's existential.

## The Domino Effect at AI Speed

Keller's central metaphor is the domino effect. A single 2-inch domino can knock down another 50% larger. By the 23rd domino, you're toppling the Eiffel Tower. By the 57th, you're reaching the moon.

The insight is counterintuitive: **success is sequential, not simultaneous**. You don't achieve extraordinary results by attacking everything at once. You achieve them by identifying the first domino—the one that makes everything else easier—and focusing relentlessly until it falls.

This principle has always been true. What's changed is velocity.

Gartner predicts that 40% of enterprise applications will use task-specific AI agents by 2026. Tools like Cursor and Claude Code aren't autocomplete engines—they're autonomous collaborators that plan, execute, and iterate. They generate code at speeds that make human typing look like carving stone tablets.

But here's what I learned from my 47-file disaster: **AI amplifies whatever direction you give it**. A weak first domino—an ambiguous spec, a poorly scoped task—cascades into thousands of lines of confident, syntactically correct, architecturally disastrous code. A strong first domino cascades into a coherent system before lunch.

The engineers who thrive in this environment won't be the ones who prompt fastest. They'll be the ones who obsess over choosing the right domino first.

## The Engineer as Chaos Engineer

There's a metaphor floating around AI thought leadership that I want to push back on: the idea of "engineer as conductor," orchestrating AI agents like musicians in a symphony.

It's elegant, but it misses something essential. Conductors work with trained professionals who follow notation and don't randomly delete production databases. That's not AI in 2026.

A better metaphor, from my world of distributed systems: **the engineer as chaos engineer**.

Chaos engineering is the practice of intentionally injecting failures into production systems to discover weaknesses before they cause outages. You hypothesize behavior, introduce disruptions, and observe results. The goal isn't to prevent failure—that's impossible. The goal is to constrain the blast radius.

Working with AI agents is remarkably similar. You're running controlled experiments against a system that will behave in unexpected ways. Your job is to:

- **Define the steady state**: What does "correct" look like before AI touches anything?
- **Constrain the blast radius**: How do you limit damage when AI goes off-script?
- **Build observability**: How do you detect when things are going wrong?

That 47-file incident? The failure wasn't Claude's. It was mine. I hadn't defined the blast radius. I gave an autonomous agent permission to touch anything that looked like validation logic, and it did exactly that.

The chaos engineering mindset would have caught this. Constrain the scope. Define success criteria. Build guardrails before you start the experiment.

## Three Lies That Will Kill Your AI Productivity

Keller identifies six lies that stand between us and success. Three of them hit differently in the AI age.

**"Everything Matters Equally"** is the first lie, and AI makes it seductive. Because AI can do almost anything, it feels like everything should get done. Why not refactor this module? Auto-generate docs? Create tests for every edge case?

Last quarter, I watched a talented engineer spend three days having AI generate exhaustive unit tests for a service we were deprecating in six weeks. The tests were beautiful. They were also worthless. Pareto's principle doesn't care about AI capabilities—20% of your decisions still drive 80% of your outcomes. The danger is drowning in AI-generated artifacts while neglecting the architectural choices that actually matter.

**"Multitasking Works"** is the second lie. Every time an AI agent displays "Generating...", there's a temptation to context-switch. Check Slack. Scan email. These micro-interruptions feel productive—"using the wait time"—but they're devastating.

Research shows developers lose ~23 minutes recovering from interruptions. A 2025 study found experienced developers using AI assistants actually took 19% longer to complete tasks, partly because the review-correct-validate cycle fragmented their concentration.

I now treat AI wait time as sacred. When the agent is working, I watch the output stream. I review context. Or I do nothing. I protect flow state like it's production uptime.

**"Willpower is Always Available"** is the third lie. AI generates possibilities faster than you can evaluate them. Every "Accept" or "Reject" decision depletes the same cognitive reservoir. By afternoon, you're accepting mediocre code just to clear the queue.

Keller recommends doing your most important work when willpower is at its peak. In AI-augmented workflows, this translates to time-blocking your highest-judgment work. I protect 7-10 AM ruthlessly for architecture and specification. AI-assisted execution happens in the afternoon, when the cost of errors is lower.

## The Focusing Question, Evolved

Keller's "Focusing Question" is the operational heart of his framework:

> *"What's the ONE Thing I can do such that by doing it everything else will be easier or unnecessary?"*

In traditional engineering, this might lead you to design the right schema or document critical decisions. In AI-augmented engineering, the answer shifts upstream.

**For most developers in 2026, the ONE Thing is no longer writing code. It's setting the context for AI to write the right code.**

At Amazon, we talk about "single-threaded leadership"—complex initiatives succeed when one person owns the problem without splitting attention. You are the single-threaded leader for your AI agent's context. If you're not shaping what the agent knows and believes, you're abdicating leadership to chance.

This means:
- **Specifications are high-leverage artifacts.** A well-crafted spec—with constraints and non-goals—is the ultimate first domino. AI works exponentially better with clear context.
- **Guardrails replace willpower.** Don't rely on "remembering" to validate. Encode standards in linters and pipelines that reject non-compliant code automatically.

The meta-question becomes: *"What's the ONE Thing I can define such that AI handles everything else correctly?"*

Usually, that's the specification. Sometimes, the architectural constraint. Occasionally, the automated test that catches AI hallucinations.

## A Counterpoint: What If I'm Wrong?

I should be honest about uncertainty.

Some colleagues believe this entire premise will be obsolete within 18 months. They argue AI is improving so rapidly that soon agents will identify the first domino, constrain their own blast radius, and manage their own context. Human judgment, they suggest, is just another bottleneck.

I'm skeptical, but I can't dismiss it.

SWE-bench shows models solving 60-70% of real-world tasks. That's remarkable. But the 30-40% of failures I see aren't random. They're tasks requiring cross-system reasoning, persistent hypothesis tracking, and organizational context that isn't in the codebase. They're the chaos engineering problems.

Until AI can model organizational history and political context, I'm betting human judgment remains the binding constraint.

## The First Domino Protocol

Here's the framework I use for AI-augmented work:

**1. Start with the Focusing Question—for AI**
Be
