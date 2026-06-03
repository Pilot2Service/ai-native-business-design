# Planning in the AI Era

*Part of the AI-Native Business Design workbook.*

This chapter turns a business idea into something an AI can build well. It ends with a *mini-PRD* — your work order for the Building chapter. When you see a prompt in a grey box, it is ready to copy and run on your own case.

> **The core idea of this chapter:** building is now fast, which means going in the wrong direction is also fast. Planning is what keeps the speed pointed at the right thing. ([short video](https://youtube.com/shorts/64fqM75OKBo?si=ugVrw-WAYkvDoyrJ))

## We now have a shared language

For most of computing history, humans had to translate their intentions into a special language for the machine — code. That translation step is largely being solved.

> **Why this matters:** increasingly, you no longer need a special machine language between you and the computer. Plain human-readable text is enough, often written as Markdown (`.md`). For the first time, the language you plan and think in is also the language the machine builds from. That is a genuinely big change — and it is why learning to write clear documents is now a core building skill.

## The biggest mistake: jumping straight into execution

The most common mistake with AI is rushing into building before thinking. Because AI work is fast, a vague request produces a fast mess. The more time you spend planning, the faster AI can help you build the *right* thing.

> **Forget the "one magic prompt" idea.** "Generate a whole website with a single prompt" is not how good work happens. An agent needs a **work order**, not half a thought. If you hand it an unfinished idea, *it* will fill in the gaps — and you will not have decided how. You should decide what AI fills in and what it does not. Create a clear path, not a guessing game that lurches forward by trial and error.

Three reasons planning genuinely matters:

- **Think for yourself first.** The plan forces you to make the decisions that matter before you spend effort building.
- **Execution is fast, so mistakes are expensive.** A wrong direction gets built quickly and at scale before you notice.
- **You prevent waste.** Good planning avoids long error-and-fix cycles, dead code, and tangled, confusing results.

## The main workflow

Keep this loop in your head for everything you build:

```
Spec  →  Plan  →  Implement  →  Test
```

- Always split implementation into small pieces.
- Always test each piece.
- Release in complete chunks, not half-finished fragments.

> **What a spec is:** short for *specification* — a clear written description of what you want to build and why, before any building starts. **What a plan is:** the ordered set of steps for actually building it. We will spend most of this chapter getting the spec right, because everything downstream depends on it.

## Start from the customer, not the technology

A spec never starts from a technical description. Even when you are building a single feature, that feature needs a reason to exist: **which customer problem does it solve?**

So begin with the customer's situation and your product vision.

**Step 1 — Write your vision in plain words.** Often the best move is to open a blank document and simply start writing:

- What does the customer need? How does the service work, and what does it do, from the customer's point of view?
- What is the customer's problem, and how significant is it?
- How is the problem solved? How does the customer use your service?
- What are your values, your principles, and where do you see the focus?

Write freely. Do not worry if it is not yet logical or well-ordered. Stream of consciousness is fine — separate paragraphs, half-formed thoughts, side points that matter. You are getting your thinking out where an AI can work with it.

**Step 2 — Create a planning partner.** Set up a project in ChatGPT or Claude and turn the AI into a thinking partner. Ask it to analyse your vision and tell you what *you* still need to define.

> **A quick word on prompting:** even for simple analysis, you get far better results when you give the AI three things — a **role** ("act as an experienced product strategist"), **context** (your vision and business), and **constraints** (what you want back, and in what form). We go deeper on prompting in the Building chapter, but use this pattern from the start. (If you are familiar with skills, add or create needed skills)

A good opening prompt for your planning partner:

```
Act as an experienced product strategist working with an early-stage startup.

Below (and in this project) is my rough product vision and customer situation.
Read it and help me sharpen it.

1. Tell me what is still vague or undefined and needs a decision from me.
2. Ask me up to 7 clarifying questions, ordered by how much they matter.
3. Point out any assumptions I seem to be making that I should check.

Do not write the plan yet — first help me think.
```

You can pass your product vision and the customer's situation back and forth for several rounds. Each round it gets sharper.

### Tools to use with your planning partner

These are well-known product techniques. Here is what each means and how to prompt for it:

- **Ideal Customer Profile (ICP)** — a clear description of the specific type of customer who has your problem most acutely and is the best fit to serve first.
  > *Prompt idea:* "Explore several customer profiles that have this problem, describe each one, and prioritise which we should serve first and why."

- **Jobs To Be Done (JTBD)** — the underlying "job" a customer is really trying to get done when they reach for a solution. It looks past the product at the customer's actual goal and situation.
  > *Prompt idea:* "Run a Jobs To Be Done exercise with me. Go deeper into the customer's behaviour and the situation in which the problem must be solved, and what they are truly trying to achieve."

- **Need themes** — short, crystallised labels for the needs underneath those jobs, both functional (what it does) and psychological (the deeper *why*).
  > *Prompt idea:* "Convert the Jobs To Be Done above into Need Themes — give 5 functional and 2 psychological themes. Return a table. Each theme should be a one- or two-word noun phrase that crystallises the essence of the need, e.g. *affordability*, *relevance*, *confidence*."

- **AI-advantage scoring** — going through those need themes and scoring where AI gives you the biggest advantage, so you focus on opportunities where AI is a real differentiator rather than a nice-to-have.
  > *Prompt idea:* "For each need theme, score from 1–5 how much advantage AI gives us in serving it, and explain the highest-scoring ones. Where is our AI advantage greatest?"

**Step 3 — Get data to support your thinking.** Use your AI tool's **deep research** mode to ground your plan in reality.

> **Deep research** = a mode in many AI tools where the AI searches many sources, reads them, and produces a structured report with references, rather than answering from memory alone. Use it to study your customer and problem more deeply, look at existing solutions and competitors, and pull in relevant market or research data.

**Step 4 — Create your PRD.** This is the central planning document.

> **What a PRD is:** a *Product Requirements Document* — a written description of what you are building, for whom, and why, including what it must do and what is out of scope. **Why it matters for AI:** a coding agent builds from your PRD the way a contractor builds from blueprints. A clear PRD produces a coherent product; a vague one produces a confused one. The PRD is how you turn your thinking into a work order the AI can act on.

What a good PRD contains:

- **The problem and the customer** — who this is for and what pain it solves.
- **The product vision** — what the experience is, in the customer's words.
- **Core features** — what the product must do, described as outcomes ("the user can…"), not as technical implementation.
- **Scope and non-goals** — and, just as importantly, **what you are deliberately *not* building** in this version.
- **Success criteria** — how you will know it works.

What a PRD does *not* need: technical architecture decisions, exact technologies, or implementation detail. Leave those to the build phase. A good PRD is clear about *what* and *why*, and leaves *how* open.

> **What separates a good PRD from a weak one:** a good PRD makes decisions. It is specific about the customer, ruthless about scope, and explicit about what is left out. A weak PRD is a wish-list that leaves the important choices for the AI to guess at.
>
> **A note on MVP scope:** your first version should be a *minimum viable product* — the smallest thing that delivers real value and lets you learn. A good MVP spec is the same PRD with scope cut hard: one customer, one core job, the fewest features that prove the idea.

**Step 4b — Create the other plans you need.** Alongside the PRD, a few supporting documents make AI building much smoother:

- **Brand style and personality** — your tone, your voice, what your product should feel like.
- **Design system** — your colours, fonts, and the basic building blocks (components) of your interface, so everything looks consistent.
- **Skills plan** — definitions of specific capabilities for your AI tools and the agents you build.

> **What "skills" are:** a skill is a reusable, packaged capability you give an AI agent — a defined task it knows how to do well, with the instructions and context it needs. Instead of describing the same task from scratch every time, you give the agent a skill. You can write your own, and you can also get ready-made ones — for example from skill libraries like skills.sh, from GitHub, or from the skill ecosystems and marketplaces of the tools you use.

**Step 5 — Build a production plan with AI.** With the spec and supporting documents in place, work out *how* you will build: in what order, what comes first, and what is left out for now. A common pattern is to set up the basic structure first — the scaffolding such as sign-in, databases, and the empty shell of the product — and then build feature by feature on top of it.

> **Scaffolding** = the basic skeleton of an app (accounts, sign-in, data storage, navigation) without real content yet. You put the frame up first, then fill it in piece by piece.

**Step 6 — Take your plans to the build agent.** Hand your PRD and plans to the AI tool that will build (for us, Lovable, in the Building chapter). Confirm the production plan and the main structural choices with it before building, and turn on any services you will need as you go. We start here in the Building chapter.

### Planning tools at a glance

- **Deep research mode** — for grounding your plan in real evidence.
- **Design tools** — for look and feel: Claude's design view, Google Stitch, Figma, and others.
- **Your AI thinking partner** (ChatGPT / Claude project) — for sharpening the spec across several rounds.

## Exercise — Write your mini-PRD

Take the opportunity you found in the Mindset chapter (or your core product idea) and turn it into a mini-PRD you can build from in the Building chapter. Run this in your AI thinking partner:

```
Act as an experienced product manager helping an early-stage startup write a
focused mini-PRD for an AI-built prototype.

Use everything you know about my business in this project, plus the opportunity
and notes from our earlier work in this conversation.

Write a MINI-PRD with these sections:

1. Problem & customer — who is this for, and what pain does it solve?
2. Product vision — describe the experience in the customer's own terms.
3. Core features — list only the few features the first version needs. Describe
   each as an outcome the user can achieve, not as technical implementation.
4. Out of scope — what we are deliberately NOT building in this version.
5. Success criteria — how we will know the prototype is working.

Keep it tight enough to prototype this week. After the draft, ask me up to 5
questions that would make the PRD sharper, then give me a revised version.
```

> Save the result. In the Building chapter you will take this PRD into Lovable and build a first working view of it.

---

*Previous: [The AI-Native Mindset](01-mindset.md). · Next: [Building: Vibe Coding in Practice](03-building.md). · By Tommi Järvinen — tommi@firstkiss.co*
