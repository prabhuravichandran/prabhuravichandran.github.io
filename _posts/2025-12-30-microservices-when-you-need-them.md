---
layout: post
title: "The Microservices Question: When Do You Actually Need Them?"
date: 2025-12-30
---

Every engineering team eventually has this conversation.

Someone suggests splitting the monolith. The reasons sound good: better scalability, independent deployments, team autonomy. Maybe a tech lead mentions Netflix or Amazon.

But here's what nobody talks about: **most teams that move to microservices regret it.**

Not because microservices are bad. But because they weren't the right solution for the problem at hand.

## The Real Cost Nobody Mentions

At Amazon, I've seen both sides. I've worked on services that absolutely needed to be split. And I've watched teams spend 18 months breaking apart a system that worked fine as a monolith.

The second group always hits the same problems:

- Debugging now spans 12 services instead of one codebase
- What was a function call is now a network request (with retries, timeouts, and failures)
- Local development requires running half your infrastructure
- "It works on my machine" becomes "it works until service D is down"

The technical debt didn't disappear. It just moved from code complexity to distributed systems complexity.

And distributed systems complexity is *harder*.

## The Question You Should Ask First

**Before** you consider microservices, ask yourself: "What problem am I actually trying to solve?"

Not the problem you think you should have. The actual, specific problem hurting your team today.

Let's look at the common reasons:

### "Our deploys are too risky"

**Microservices answer:** Split into services so teams can deploy independently.

**Simpler answer:** Feature flags. Canary deployments. Better testing.

If you can't deploy a monolith safely, you won't deploy microservices safely either. You'll just have more things to deploy unsafely.

### "We can't scale"

**Microservices answer:** Split services so we can scale them independently.

**Real question:** Which *specific* part can't scale?

If it's your database, microservices won't help—you'll just have multiple services hitting the same bottleneck.

If it's a specific function, pull *that* out. One service. Solve the actual problem.

### "Teams keep stepping on each other's code"

**Microservices answer:** Give each team their own service.

**Simpler answer:** Better module boundaries. Clear ownership. Code reviews.

Conway's Law works both ways. If your team structure is messy, your microservices will be messy too. Fix the organization first.

## When Microservices Actually Make Sense

I'm not anti-microservices. But there are real, specific conditions where they're the right choice:

**1. You have a genuinely different scaling profile**

At AWS, we had a service that handled millions of lightweight requests per second, and another that processed heavy compute jobs. They belonged on different infrastructure. They needed different scaling strategies.

That's a real reason.

**2. You have strong team boundaries**

When you have 50+ engineers, and teams are organized around business capabilities (not technology layers), microservices can create clarity.

But "strong team boundaries" means:
- Teams can make decisions independently
- They own the full stack (not just "the API layer")
- They're measured on outcomes, not features shipped

If you don't have this, microservices will just create coordination overhead.

**3. You need different technology for different problems**

Maybe your main app is in Java, but you need ML inference in Python. Or you're processing streaming data with different requirements than your API.

This is valid. But ask: do I need a *different* service, or just a different library?

## The Path Most Teams Should Take

Start with a well-structured monolith.

Not a ball of mud. A monolith with:
- Clear module boundaries
- Dependency rules that are enforced
- Different modules that could *become* services later

Think of it as "microservices without the network calls."

You get:
- Fast iteration (everything's in one place)
- Simple debugging (stack traces work)
- Easy local development
- The option to split later *when you have a real reason*

And when that day comes—when you *actually* need to split something out—you'll know exactly which boundary to split along.

## The Test

Here's how you know you're ready for microservices:

**Can you answer these questions with specifics?**

1. Which *exact* part of the system needs to scale differently, and by how much?
2. Which team owns this service end-to-end, and how will they operate it independently?
3. What happens when this service is down? (Be specific. Not "we'll handle it gracefully.")
4. How will you test changes that span multiple services?
5. How will you debug issues in production?

If you can't answer these clearly, you're not ready.

And that's okay. Most systems don't need microservices.

## What's Next

This is **Part 2** in my series on keeping systems simple.

- Part 1: [The Cost of Complexity](https://prabhuravichandran.github.io/2025/12/23/hello-world.html)

Coming up:
- **Part 3:** Patterns that reduce complexity (not hide it)
- **Part 4:** Real AWS examples that chose simplicity
- **Part 5:** Why the best code is deleted code

**The bottom line:** Microservices solve specific problems. Make sure you have those problems before you accept the complexity they bring.

Because once you split a monolith, there's no going back.

---

*Prabhu Ravichandran is a Senior SDE at Amazon, where he's built both monoliths and microservices—and learned when each makes sense.*
