# Building: Vibe Coding in Practice

**Business-first · No coding background required**

The Mindset and Planning chapters were about thinking: seeing AI as a new way to build a company, and turning a business idea into documentation an AI can build from. The output of that work is a **PRD**. This chapter is where you build — you take that plan into a real tool, **Lovable**, and turn it into something you can click, share, and test.

When you see a prompt in a grey box, it is a **template**: replace anything in `[square brackets]` with your own project, and never leave example wording in a prompt you send. Each part ends with an exercise you run on **your own** case.

> **You need a PRD to start.** From the Planning chapter you should have a *spec* (what you are building and why) and a *mini-PRD*. That PRD is the starting fuel for the build. If it is thin, that is fine — you will improve it as you go.

---

## How this chapter is organised

- **Part 1 — Vibe Coding in Practice.** What AI-assisted building is today, what a production environment actually contains, and how to open a new project in Lovable.
- **Part 2 — Tools, Prompting and Processes.** The everyday loop of building, fixing, and iterating without falling into error-fix loops. The longest, most practical part.
- **Part 3 — Bring Your Idea to Life.** You build a first view of your own product, learn how to release safely, and define your next steps.

---

## Part 1 · Vibe Coding in Practice

You do not need to write code. You need a clear vision and the ability to describe it well. We cover how to build in small, testable slices, how to manage context across sessions, and how to use Lovable to go from PRD to a working prototype in minutes. We also cover how to manage a vibe-coding project.

### What "vibe coding" actually means today

The term has an underrated reputation, and that reputation is out of date. The tools move so fast that vibe coding is not what it was a year ago.

The important correction, and it connects straight back to the Planning chapter: **vibe coding is not waving vaguely at what you want and hoping.** It is a systematic process. When you have the cycle below firmly in hand, the output is genuinely good.

```
spec  →  build  →  test  →  (learn)  →  spec  →  build  →  test ...
```

You describe a small, well-defined slice. The tool builds it. You test that it works. You learn, then describe the next slice. The discipline is in keeping each loop small and testable — not in writing code.

> **The three tool families.** Coding agents come in three shapes, and you pick by comfort level and preference:
> - **CLI** (command-line) — a terminal where you type instructions. Most powerful, least friendly for non-coders.
> - **Web / app** — a browser or desktop app you talk to. This is where **Lovable** lives, and where most of you will work.
> - **IDE** — a code editor with an AI built in. For people who want to see and touch the code.
>
> **This guide uses Lovable**, which lives in the web/app family — you never have to open a terminal. The principles and the prompts apply just as well to other AI build platforms such as Bolt, v0, Replit, Cursor, or Claude Code. Where a step is specific to Lovable, adapt it to whatever tool you use.

### A platform is more than a code agent

Here is the big picture I most want you to leave with today. When you choose a Lovable-type platform, you are not just renting a thing that writes code. You are getting a **production environment**.

A real, production-ready product needs many parts that have nothing to do with writing code:

- a **database** to store users, content, and orders;
- **login and accounts** (authentication) so people can sign in;
- **payments**, if you charge money;
- **email sending** for confirmations, resets, and notifications;
- **security** so data is protected;
- a **domain** (your `yourcompany.com` address) and hosting so the world can reach it.

Traditionally, assembling all of that from a prototype into a launched product is exactly the work that required a developer. The shift is this: platforms like Lovable bundle most of these in. Cloud features, AI connections, a payment path, login systems, security modules, hosting and domains — they come with the environment.

> **What this means for you:** you can go from idea to a live, paying-capable product without hiring someone to "wire it all up" first. You still need to think clearly and decide what your product does. You no longer need a coder to glue the plumbing together.

### What do you need ready before you start?

It depends on how far you want to go. Three honest levels:

**Level 1 — Play and test.** You just want to feel how it works.
- *Content needed:* a few notes describing your idea (even rough ones).
- *Architecture needed:* nothing. Open Lovable, switch to plan mode, and start prompting.

**Level 2 — A working prototype you can put in front of customers.** This is our target today.
- *Content needed:* a **PRD**, a rough **production plan**, **design system specs**, **brand specs**, and **MVP specs**.
- *Architecture needed:* a Lovable workspace set up, a GitHub repo, and a clear idea of what data you store.

**Level 3 — A production-grade product.** Real users, real money, real reliability.
- Everything in Level 2, plus serious attention to security, payments, data, releases, and support.

> We aim at **Level 2** today: something good enough to show customers and learn from.

### Your working setup for Level 2

Four things sit on your desk while you build:

1. **Lovable** — your building tool. Before you start, set up your workspace and put your documents where Lovable can read them (more on this just below).
2. **A building-assistant AI** — a *separate* project in **Claude** or **ChatGPT** that shares as much of the same context as your Lovable agent. This is your second brain: it improves your prompts, reviews Lovable's plans, and gives a second opinion. We use it constantly today.
3. **A GitHub (or GitLab) account** — every change is saved to a *repository* ("repo"), which is a versioned history of your project. Lovable connects to it for you. This is your safety net: you can always go back.
4. **An issue tracker like Linear** (or even a simple list) — to keep your own work and the build process organised, so you always know the next thing to do.

> **What is a repo?** A repository is a project's full history, saved step by step. If a change breaks something, you can roll back to a working version. You do not manage it by hand — Lovable and GitHub handle it. You just need the account connected.

### A tour of the Lovable environment

The parts of the Lovable environment worth knowing:

- **Plan mode and Build mode.** Plan mode thinks and proposes; Build mode actually makes changes. **Always plan before you build.**
- **Connectors.** How Lovable links to outside services (database, payments, email, and more).
- **Customisation — this one matters most.** This is where you give the project its lasting context so every prompt starts from a shared understanding.
  - **Knowledge** — a plain **text field** (not a file upload) that is sent with every prompt. You paste your condensed core context here: a short PRD summary, MVP scope and non-goals, design rules, and key terms. See the note below on how to handle full files.
  - **Skills** — reusable instructions and ways of working, loaded when a task calls for them.

> The single biggest quality lever is **context**. A prompt sent into an empty project gets a generic answer. The same prompt sent into a project that already knows your PRD, your brand, and your constraints gets an answer that fits *your* business.

### How to start: the opening prompt

When you are in your workspace, you can simply begin. But a good **opening prompt** sets the tone for the whole project. The principle has five parts:

1. **Give rich context** — who this is for, what the product does, what matters.
2. **Give a clear task and a target output** — what you want to see at the end of this step.
3. **Give working principles** — e.g. a *simple and robust* architecture, reliability, dependability, and good documentation.
4. **Use PLAN mode first** — always.
5. **Forbid building until the plan is good** — make it propose a plan and wait for your approval.

> **Read this before copying any prompt below.** Every prompt in this document is a **template, not finished content.** Anything in `[square brackets]` is a placeholder you must replace with your own project. **Never send a prompt that still contains example wording** — an invented product, sample features, or made-up data. If you leave it in, the agent will faithfully build *that* instead of your idea. Read each prompt line by line and make sure every word is true for your case.

> If you have not worked this way before, expect the first plan-mode reply to be a list of questions and a proposed plan — not a finished product. That is exactly what you want.

#### Opening prompt — explore an idea (the lightest start)

Replace the bracketed part with your own idea, then send it:

```
I want to explore an idea, not build production software yet.

Idea: [describe your idea in 2–3 sentences: what it is, who it's for, and
the one thing it should let someone do].

Please stay in PLAN mode. Propose the simplest possible version: what
screens it needs, what information we store, and the smallest first slice
we could build to see it working. Do not build anything yet — show me the
plan and wait for my go-ahead.
```

#### Important: Knowledge is text — so how do you give Lovable your files?

Here is a detail that trips up nearly everyone on a fresh workspace: **the Knowledge area in settings is a text box, not a file upload.** You cannot drop your `PRD.pdf` into settings. So how does your documentation reach the agent? Two complementary routes, and you use both:

1. **Paste the essentials, as text, into Knowledge.** This is your *permanent* context — it is sent with **every** prompt. Put a condensed version here: a short product summary, the MVP scope and non-goals, your design rules, and key terms. (There is a character limit, so condense rather than dump.) You don't have to write it yourself — the recommended opening prompt below drafts it for you.
2. **Attach the full files to your prompt.** Lovable *does* let you drop files into the chat, and it reads them as context for that message — PDFs, spreadsheets (CSV/XLSX), slide decks (PPTX), images, and more. So your full `PRD.pdf`, wireframes, and brand guide go in as **attachments to your first prompt**, not into settings.

> **The key difference:** text in the Knowledge field is *persistent* (every prompt sees it); a file attached to a prompt is context for *that conversation*. So put the durable rules in Knowledge as text, and attach the heavy source documents when you need them.

**Should you write the file names into Knowledge?** You can, as a pointer — *"Source-of-truth documents (attached when relevant): PRD.pdf, design-system.pdf"* — but be clear about what it does: naming a file only tells the agent the file *exists*, it does **not** load its content. The content must be pasted as text or attached to a prompt. (For a more durable home for full documents, see the advanced section on keeping a `/docs` folder and an `AGENTS.md` in your repo.)

You don't have to write that text yourself. The recommended opening prompt below asks the agent to **compile the Knowledge text for you** from your attached files, so you can paste it straight into settings.

#### Recommended opening prompt for a new workspace (Level 2)

This is the one to use on a fresh workspace, because it matches how Lovable actually works: the full files are attached to the message, and the agent compiles the Knowledge text *for you* to paste into settings. Replace everything in `[brackets]` with your own project — and make sure nothing example-like is left behind.

```
We are starting a new project called [PROJECT NAME]. In it we create
[one or two sentences: what the product is, and who it is for].

I've ATTACHED the source documents to this message: [list them — e.g. PRD,
design system, wireframes]. I can't upload files into the project's Knowledge
settings (that's a text field only), so they are here as attachments.

Stay in PLAN mode and do NOT build anything yet. Please:
1) Read the attached files first.
2) In one short paragraph, tell me back what you understood the product to
   be, who it's for, and what's in scope. If anything is unclear or the files
   disagree, ask me — don't guess.
3) Propose a milestone plan (a short list, Milestone 1 → N), then a detailed
   plan for starting Milestone 1 only.
4) Compile a concise KNOWLEDGE section I can paste into this project's
   Knowledge settings: product summary, who it's for, the data we store, key
   terms, design rules, and a clear list of non-goals. Give it to me as plain
   text, in short bullet rules, that I can copy and paste.

Wait for my approval before building.
```

> **Why this works so well.** It does four jobs in one move: it loads your *real* context (so there are no invented details to clean up), it makes the agent *say back* what it understood — so you catch misunderstandings while they still cost nothing — it produces a milestone plan instead of a blind build, and it hands you the Knowledge text to paste, solving the "I can't upload files" problem in the same breath.

If you want to hand the agent explicit **working principles** too, add a block like this. It contains no project specifics, so it is safe to reuse as-is:

```
WORKING PRINCIPLES
- Keep the architecture simple and robust; prefer reliable, well-supported
  building blocks over clever ones.
- Reliability over features — it must not break on basic use.
- Build in small, testable slices and tell me how to test each one.
- Document as you go.
- Don't change anything outside the current milestone's scope.
```

### What a typical build plan looks like

When you ask the agent for a milestone plan, it helps to know the shape a good one usually takes. Real products tend to be built up in roughly this order. The names matter less than the logic: **get the shape and the central thing right early; add money, accounts, and outside services later; polish last.**

0. **Setup / foundation.** The plumbing: workspace, the connected repo, the database, and the bare scaffolding for accounts. Nothing visible yet — this is the ground the rest stands on.
1. **Skeleton & design.** The shell of the product: navigation, page layout, and your design system applied to empty screens filled with realistic sample content. The goal here is that it *looks* right before it *works* — this is what kills the "AI slop" feel early.
2. **Canonical elements.** The one central thing your product revolves around — whatever your core object is (for instance a record, a listing, a booking, a post) — built end to end on real data: created, saved, and shown back. Get this representative core object solid and everything after it has a pattern to follow.
3. **The core flow (happy path).** The main journey a user takes, working start to finish when everything goes right: the single path that delivers your product's core value.
4. **Supporting states & flows.** The unglamorous parts that make it trustworthy: empty states, error messages, confirmations, and the obvious edge cases (an empty list, a blank required field, a duplicate entry).
5. **Accounts & permissions.** Login, and who is allowed to see and do what — for example, an owner sees everything, while a regular user sees only their own data.
6. **External services.** Payments, email confirmations, and any integrations. These come *after* the core works, because they are easier to wire into something already solid.
7. **Polish, metrics & hardening.** Final design polish, the internal metrics that show how customers behave, a security and privacy pass, and up-to-date documentation.
8. **Release.** Tested in your development environment, then published — a clear, deliberate release rather than a trickle of half-finished edits.

> **What "canonical elements" means.** It is the representative, core building block your product is really about. Build it once, properly, and it becomes the template for everything similar that follows. Getting it right early is far cheaper than discovering halfway through that the central object was modelled wrong.

You do not have to follow this exactly — a throwaway prototype might stop at milestone 2. But it is the backbone of how a production plan is built up, and it is what a good plan from your agent should broadly resemble. To get yours:

```
Based on our PRD and MVP scope in this project's knowledge, propose a
milestone plan for building this product in order, from setup to first
release. For each milestone, give a short name, one sentence on what it
delivers, and what I will be able to click and test when it is done. Keep
each milestone small enough to test on its own. Don't build anything yet —
just the plan, so I can approve the sequence.
```

> **Exercise (Part 1).** Open Lovable. Paste a condensed version of your PRD into the project's **Knowledge text field** (or ask Lovable to draft it from your attached PRD), and have your full documents ready to **attach to your first prompt**. Write your own opening prompt using the structure above, run it in **plan mode**, ask the agent for a **milestone plan**, approve the sequence, then build **Milestone 1 only**. Test that it works before moving on.

---

## Part 2 · Tools, Prompting and Processes

Use the right tool at the right stage, and learn how to talk to AI so you get useful results. We cover the core stack — Claude, Lovable, GitHub, Google AI Studio, and your second AI assistant — and the design and prompting principles that make the biggest difference in practice.

### The everyday loop

Almost all of your time will be spent in two phases, alternating:

1. **The active build phase.** You follow the build plan (Lovable's, or one you and your AI assistant shaped together). The product rises piece by piece, and **you test each slice as it lands.** This is calm, predictable work when the plan is good.

2. **The iteration phase.** You either fix something that is wrong, or add something new. The rule here is simple and easy to forget:

> **Always define and bound the problem before you prompt.** Careless, vague iteration is the number-one cause of *error-fix loops* — where each fix breaks something else and you spiral. A bounded, clearly described change almost never loops.

### How to fix and change things well

When something is wrong, your job is to give the agent **real context** — and to ask it what it needs to identify the problem. There are six ways to give context, from lightest to heaviest. Reach for the lightest one that will work:

1. **Describe it in words.** *"In the Dashboard view, the header element is misaligned. Right now it sits flush left and overlaps the logo; it should be centred with even spacing on both sides."*
2. **Show it.** Add a screenshot — and still explain the screenshot in words. A picture without words is half a message.
3. **Select the element in the preview.** Lovable lets you click an element in the preview to pull it directly into the chat, then write about the problem.
4. **Give log information.** Logs from Lovable, from connected services, or from the browser (View → Developer Tools). Logs are how you turn "it's broken" into "here is exactly what failed."
5. **Point at the files.** Name or attach the file(s) where the error — or its cause — likely lives.
6. **Expand the context.** When the small ways are not enough, widen out: relevant screens, related data, and the recent changes that might be involved.

> **Always run your building-assistant AI alongside.** Your second AI project (in Claude or ChatGPT) can find the problem independently, or verify that Lovable's fix plan is correct and complete. Cross-checking two plans against each other catches mistakes that either one alone would miss. Remember: the second AI also needs good context to give a wise second opinion.

#### Example prompt — a layout change (move the menu from the header to a sidebar)

```
SCOPE: layout only. Do not change any features, data, or styling colours.

WHAT I WANT
Move the main navigation from the top header into a left-hand sidebar.

DETAILS
- The sidebar should be fixed on the left, full height, with the same menu
  items currently in the header, in the same order.
- The header keeps only the logo (left) and the account icon (right).
- On a narrow/mobile screen the sidebar should collapse into a button that
  opens it.

PROCESS
Stay in PLAN mode first. Tell me which screens and files this touches and
anything that could break. Then wait for my approval before building.
I'm attaching a screenshot of the current header so you can see what moves.
```

#### Example prompt — root-cause investigation (a reusable skeleton)

Copy this and drop your own situation into the brackets:

```
I have a bug and I want the ROOT CAUSE, not a guess.

WHAT HAPPENS
[Describe the wrong behaviour: what you did, what you expected, what
actually happened.]

WHERE
[Which screen / view / step. Attach a screenshot if you have one.]

EVIDENCE
[Paste any error messages or logs. From Lovable, from a connected service,
or from the browser console — View → Developer Tools → Console.]

WHAT I'VE ALREADY TRIED
[Anything you tested or changed, and what happened.]

WHAT I NEED FROM YOU
Before proposing a fix: tell me what is most likely causing this and why.
If you need a specific file, log, or screenshot to be sure, ask me for it
rather than guessing. Then propose a minimal fix and how I can test it.
```

#### Example prompt — cross-evaluating a fix plan with your second AI

Paste Lovable's proposed fix into Claude or ChatGPT:

```
Attached is Lovable's proposed fix plan for this problem:

PROBLEM: [one or two sentences]
LOVABLE'S PLAN: [paste it]
RELEVANT CONTEXT: [the screen, the data involved, recent changes — and
whatever from my PRD/brand is relevant]

Please analyse this plan critically:
1. Does it actually solve the stated problem?
2. Has it identified the real root cause, or is it patching a symptom?
3. What could it break elsewhere?
Do you need any files, logs, or screenshots to evaluate it properly? If so,
tell me exactly what to send. Otherwise, give me your verdict and any
changes you'd make.
```

### Changing small details — bound the work tightly

When you want a precise change, give a precise scope and **forbid the agent from touching anything else.** Clear instructions, clearly stated. Here is the shape of a good one, using a real example:

```
SCOPE: the appearance of a single list-item row in the Dashboard. Nothing else.

The dashboard list-item row has too much information and is hard to read.

DO THIS
- Remove fields X and Y from the row.
- What remains is A, B, and C.
- A is the field attention should land on: use the brand's accent colour
  (see brand specs in knowledge).
- B and C are secondary information: use the light tones from our design
  system.

DO NOT
- Do not change any other element, screen, data, or behaviour.
- Do not restyle the rest of the list or the page.

I'm attaching a screenshot of the current row. I'm also attaching a
reference screenshot — please make the row resemble this style.
```

> Reference screenshots are powerful. *"Make a list-item row like this, in this style"* gives the agent a target it can match far better than words alone.

### Testing and evaluation — small and often

After every build slice, do a quick, ordinary test before moving on. You do not need a test plan; you need the habit. Click the thing you just built. Try the obvious path. Try one slightly wrong input (a blank field, a silly value). If it holds, move on. If it breaks, you have caught it while the change is small and easy to trace.

Beyond manual clicking, you can have AI help you evaluate. An **evaluation prompt** asks an AI to stress-test your work:

```
Here is what this screen is supposed to do: [describe it].
Acting as a careful first-time user, list the ways this could confuse or
break: unclear steps, missing feedback, empty/edge inputs, and anything a
non-technical user might get stuck on. Rank them by how likely and how
damaging each is, and suggest the smallest fix for the top three.
```

### Keeping documentation alive in Lovable

Documentation is not bureaucracy — it is the context your future prompts depend on. Ask Lovable to write and update it as you go.

```
Update the project README to reflect what we've built so far. Include:
what the product does, the main screens and what each is for, what data we
store, and any decisions we made and why. Keep it short and in plain
language a non-technical founder could follow. Then tell me what changed
since the last version.
```

A good practice: ask for a documentation update at the **end of each working session** and after any significant feature. The cost is one prompt; the payoff is that every future conversation starts from a clear, current picture.

### Keeping the code clean

As you progress, your repo collects old and unused pieces — abandoned experiments, replaced screens, dead bits. Left alone, this clutter confuses both you and the agent. Clean it deliberately:

```
SCOPE: cleanup only. Do not add features or change how anything works for
the user.

Review the project for code, files, or screens that are no longer used or
reachable. Before removing anything, list what you found and why you believe
it's unused, and wait for my approval. After I approve, remove them and
update the documentation. We should be able to confirm nothing user-facing
changed.
```

### Managing external services — connectors, APIs, and MCP

Your product rarely lives alone. It talks to other services: a database, a payment provider, an email sender, sometimes an AI model. Three words you will hear:

- **Connector** — a ready-made link inside Lovable to a common service (often a few clicks, no setup code).
- **API** — the doorway a service exposes so other software can talk to it. When there is no ready connector, you connect through an API.
- **MCP** — a newer, standard way to give an AI agent access to tools and services so it can act through them. Think of it as a universal adapter for AI.

> You do not need to understand the internals. You need to know *what* you are connecting and *why*, and to let your AI assistants handle the wiring while you confirm each connection does what you intend.

### Getting out of error loops

If a fix breaks something, which breaks something else, **stop prompting.** Loops feed on momentum. To break out:

1. **Roll back** to the last known-good version (this is why the GitHub repo matters).
2. **Re-bound the problem** in one clear sentence.
3. **Get a second opinion** from your other AI before trying again.
4. **Change one thing**, then test, before changing the next.

### When you don't understand what the agent is doing

This will happen, and it is not a problem. The agent's plan will sometimes read like another language, or it will hand you a vague instruction like *"connect your GitHub repository here"* and assume you know what that means. The skill you are building is not understanding the technology — it is **knowing how to ask until you understand enough to decide.** A good agent is an endlessly patient explainer; use that.

Two common situations and what to do:

**The plan is too technical.** Don't approve it on faith and don't pretend. Ask for it again in plain language:

```
Explain this plan to me as if I'm a smart but non-technical founder. For each
step: what it does in plain words, why it's needed, and whether it could be
undone later if we change our minds. Flag any step that touches money, user
data, security, or who can access what — I want to understand those before we
proceed. Avoid jargon; if you must use a technical term, define it in one line.
```

**The instruction is vague or assumes knowledge you don't have.** Ask for it as concrete, numbered steps for *your* exact situation:

```
You told me to "connect my GitHub repository." I've never done this. Walk me
through it as numbered steps for my exact situation: what I click, where, and
in what order, and how I'll know it worked. Assume I'm starting from scratch,
and explain any term you use as you go.
```

Your **building-assistant AI** (Claude or ChatGPT) is your best translator here, because you can ask it anything without spending Lovable credits, and you can keep asking until it clicks:

```
Here's something Lovable said that I don't understand: [paste it].
Explain it like a patient mentor talking to a non-technical founder: what it
means, why it matters for my product, what I actually have to do, and what
happens if I get it wrong. Then give me 2–3 good questions I could ask Lovable
to make sure it does this safely.
```

A few questions that pull understanding out of any agent, on any topic: *"Why is this needed?"* · *"What happens if we don't do it?"* · *"Can this be undone later, or is it permanent?"* · *"What decision are you actually asking me to make?"* · *"What could go wrong, and how would I notice?"*

#### Can you just trust the agent if you don't understand at all?

Honest answer: **it depends entirely on whether the action is reversible.** Split everything into two buckets.

For **low-stakes, reversible, cosmetic** work — layouts, colours, copy, a new screen, most ordinary building — yes, you can let the agent run and judge it by the result. If you don't like it, you change it or roll back. Your connected repo and your habit of clear, tested releases are exactly the safety net that makes this safe. You do not need to understand *how* it works to decide *whether you like* what it produced.

For **consequential or hard-to-undo** things, no — understand enough to make the call first. These include anything that touches **money** (payments, billing), **user data** (especially deleting it), **security**, **who can access what** (permissions and sharing), connecting **accounts or credentials**, or **publishing to the public**. "I didn't understand it" is never a good reason to approve something you cannot take back.

> **The rule of thumb:** never approve something *irreversible* just because you'd rather not ask. For everything reversible, experiment freely — trying, looking, and rolling back is how you learn fastest. The whole point of the repo and staged releases is to make "just try it" safe for the things where trying is cheap.

> **Exercise (Part 2).** Two parts. **(a)** Ask Lovable to create or update your project's context documentation. **(b)** Take a weak prompt you might naturally write — e.g. *"make the dashboard better"* — and rewrite it into a strong one using **role, context, and constraints**, with a clear scope and an explicit *do-not* list. Run the strong version and compare the result.

---

## Part 3 · Bring Your Idea to Life

This is where everything comes together on your own idea: finish your PRD, build a first view in Lovable, and define your next concrete steps.

### Evaluating with AI before you ship

Before showing anything to a customer, let AI pressure-test it. A few evaluation moves:

```
You are a sceptical first customer for this product: [one line about who].
Walk through the main flow [name it] and tell me where you'd hesitate,
get confused, or give up. Then switch roles and act as a careful reviewer:
check the flow for broken steps, missing confirmations, and empty/edge-case
inputs. Give me a prioritised list of what to fix before I show this to a
real customer.
```

You can run evaluation prompts against your second AI as well as Lovable, and compare what each one flags.

### A simple, safe release strategy

Build and test in a **development environment** first. Only when a slice is tested do you publish. Good releases share a few traits:

- **Make clear releases** — bundles of changes you have actually tested and confirmed work, not a constant trickle of half-finished edits.
- **Respect existing users in big changes.** If you already have people using the product, warn them before large iterations, and make sure they do not lose anything essential (for example, if you remove a feature).
- **Make incremental versions** so users can move from version 1 to version 2 in a controlled way, rather than waking up to a product they no longer recognise.

### How building actually goes now that everything is fast

This is the honest map of how products take shape today.

#### Prototyping

You experiment and test everything until the project hits a knot. That is not failure — it is learning. By the time you are stuck, you usually know one of three things: how to solve the problem, what real work lies ahead to do it properly, or that it is not worth doing at all.

In prototyping, **lean on the old and the proven.** Reuse working pieces. Use ready-made templates and tweak them into your own. Move fast.

> **A warning about look and feel.** Prototypes are almost always *"AI slop"* — they look and feel like a generic AI-built proto. That is fine for testing an idea internally. It is not fine for a customer.

#### MVPs that go to customer testing

These need a more thorough spec and plan than a throwaway proto. And critically: **bring your own design system.** Either model an existing design you trust, or create a unique look for this product. This single step removes the immediately-noticeable "AI slop" effect and makes you credible at first glance.

Build in **internal metrics** so you can see how customers actually behave:

```
Design simple internal metrics and tracking for this product so I can
understand real customer behaviour: how the product is used, where people
drop off, and which actions matter most. Tell me what to measure, where to
place the tracking, and how I'll read the results — in plain language, for
a non-technical founder.
```

### Practical experience: how the work really flows

A few hard-won patterns from building with coding agents, from a service-development point of view.

**Keep a bigger production plan and backlog running the whole time.** The day-to-day is small slices, but you steer by the larger plan.

**Expect to move through several prototypes.** If you start by prototyping, you usually progress like this:
- **Proto A** — test whether thing A is even possible.
- **Proto B** — test whether you can get an agent (or a flow) to reliably produce the result you want; often a "pipeline" or "flow" proto.
- From these learnings, your **MVP definition** sharpens — sometimes into several MVP experiments.

**Then make an MVP.** There is more than one kind:
1. **Minimal MVP** — does the one core thing, everything else cut. The traditional MVP.
2. **Hypothetical MVP** — the feature set your PRD assumes is right.
3. **Fan / expanded MVP** — deliberately *too many* features. Because building is now cheap, you ship extras specifically to learn from users which ones are relevant and which are not.

**Development moves in a chain of diamonds.** Expansion (explore widely) and focus (narrow down) phases follow each other, again and again, until customers teach you what the real, attractive product actually is. *(Note: this is learning the product, not yet product–market fit.)*

**Hold a release path** as your spine:

```
MVP → MVP+1 → MVP+2 → … → Beta → Beta+1 → …
```

Each step is a tested, releasable point you can show, learn from, and build on.

> **Exercise (Part 3).** On your own case: finish your PRD, build a **first view** of your product in Lovable, and write down **three concrete next steps**. If it helps, prepare a **60-second** spoken summary of what you built and why — a good discipline for when you pitch it later.

---

### Building efficiently: getting the most out of your Lovable credits

Lovable runs on **credits**, and as a beginner the fastest way to lose them is to treat Lovable as a place to think out loud. It is not. It is a place to *implement things that are already decided*. Almost every credit-saving habit comes back to that one idea.

> **What is a credit?** A credit is what Lovable spends each time the AI does work for you. The cost scales with complexity: a tiny styling tweak is cheap, generating a whole new screen is not. Plan-mode conversations are cheaper than build/agent-mode changes. Exact prices and your free allowance change over time — check Lovable's current pricing, and watch your balance in the dashboard.

A practical checklist for spending credits wisely:

1. **Do the messy thinking outside Lovable.** Brainstorming, drafting, and rewriting prompts belong in your free building-assistant AI (Claude or ChatGPT), not in Lovable's chat. Arrive at Lovable with a decision, not a question.
2. **Plan before you build.** Use plan mode to lock the approach before any build happens. A good plan turns five exploratory build attempts into one clean build.
3. **Be hyper-specific.** Vague prompts cause retries, and every retry costs credits. The bounded, scoped prompts from Part 2 are also your cheapest prompts — precision and economy are the same skill here.
4. **Batch related changes into one structured prompt.** Five small "oh, and also…" messages cost more than one well-organised request that lists everything at once.
5. **Use free, no-credit edits for small tweaks.** Visual edits / manual edit mode for text, colours, and spacing typically cost nothing — use them instead of prompting the AI for cosmetic changes.
6. **Decide the data and structure before the first generative prompt.** Restructuring the database or architecture mid-build is one of the most expensive things you can do. Think it through (with your assistant AI) up front.
7. **Find the root cause before you write a correction prompt.** This is the big one. One corrective prompt aimed at the real cause beats five hopeful retries. Use the root-cause prompt from Part 2, and have your second AI confirm the fix plan *before* you spend a Lovable credit on it.
8. **Break large features into small, verifiable steps.** A big "build the whole dashboard" prompt that fails wastes more than several small steps, each tested as it lands.
9. **Start from a template close to your goal, then modify.** Adapting something that already works is cheaper than generating from scratch.
10. **Use the built-in "Try to fix" option** for routine system errors when Lovable offers it, before crafting a manual fix prompt.

> **The mindset in one line:** credits reward *clear thinking*, not *fast typing*. Every habit above is really the same move — decide cheaply (in your assistant AI and in plan mode), then spend credits only to implement what you have already worked out.

---

### Advanced: the knowledge base, guardrails, and your source of truth

> **This is an advanced, optional section.** It goes deeper than a first prototype needs — skim it now, and come back when you want to push toward something more controlled and production-minded.

So far we have put only PRD- and design-style content into the project's knowledge. That is the right start — but knowledge is capable of much more. It is where you turn the agent from "a clever helper that forgets" into "a teammate that reliably follows *your* rules." Think of everything here as building a **source of truth** the agent reads before it acts.

#### How Lovable actually takes in context

It helps to know what the agent reads on every message, because that tells you where to put each kind of material:

- **Project knowledge** — a text field for *this* project: what it does, who it is for, its data model, its constraints. Always in context.
- **Workspace knowledge** — a text field shared across *all* your projects: coding standards, preferred libraries, architectural rules, brand voice. Define your reusable **guardrails** here once and every project inherits them. Always in context.
- **Skills** — instructions loaded *on demand*, only when a task matches them (a release checklist, a way of drafting customer-facing copy, a specific content format). Knowledge is always on; skills are situational.
- **Integration knowledge** — context pulled in automatically from the services you have connected.
- **Instruction files in your GitHub repo** — for more technical users, a root-level `AGENTS.md` or `CLAUDE.md` file is read by the agent. These are general, widely-used conventions for steering coding agents, not Lovable-specific inventions.

> **Your question answered — is a docs/guardrails section there automatically?** No. The knowledge fields are blank text boxes you fill in yourself. Repo instruction files like `AGENTS.md` and `CLAUDE.md` are read *automatically only if they exist* — you (or Lovable, on request) create them first. Likewise, Lovable will happily maintain a `/docs` folder in your repo as living documentation, but it does not appear on its own; you ask for it. Nothing steers the agent until you put something there.

#### What belongs in your source of truth

Beyond the PRD and design system, consider adding materials like these. Match each to the right home (project knowledge for product-specific truth, workspace knowledge for reusable standards, skills for situational playbooks):

- **Product truth and non-goals** — the MVP scope *and an explicit list of what you are deliberately NOT building*. Non-goals prevent the agent from "helpfully" expanding your product.
- **Design system and brand** — colours, typography, spacing, which component library to use, and the tone of UI copy. (*Project* if unique to this product; *workspace* if shared.)
- **Architecture rules** — "keep it simple and robust," preferred libraries, where data access lives, patterns to follow and patterns to avoid.
- **Data model / schema** — your key tables and fields, how IDs work, how money is stored. The agent makes far fewer wrong assumptions when it knows your data shape.
- **Domain glossary** — your terminology, so the agent uses *your* words consistently (a "booking" vs a "reservation" vs a "slot").
- **Coding standards** — naming, strict typing, no dead code, no placeholder "lorem ipsum." Best kept in *workspace* knowledge.
- **Security and privacy requirements** — what data is sensitive, what must never be exposed in the UI or logs, and your authentication rules.
- **Testing / definition of done** — e.g. "verify in the browser before marking complete; remove unused code." This is a quiet but powerful quality guardrail.
- **Negative guardrails — the "do not" list** — explicit prohibitions: do not change unrelated files, do not restructure the database without asking first, do not introduce new dependencies without flagging them.
- **External references** — links to API docs, integration endpoints, internal tools.
- **Release and versioning conventions** — your `MVP → MVP+1 → … → Beta` path and how existing users are protected during big changes.
- **A decision log** — short notes on *why* key choices were made, so the agent does not quietly undo a deliberate decision later.

> **Keep it tight.** Each knowledge field holds a limited amount of text, and in very long conversations even always-on instructions can slip. Favour short bullet rules over long paragraphs, write it like onboarding notes for a new teammate, and review it whenever your stack or direction changes.

#### Prompts for building your source of truth

**Draft a project-knowledge block from your PRD:**

```
Read the PRD and brand notes in this project's knowledge. From them, draft a
concise PROJECT KNOWLEDGE block I can paste into Lovable's knowledge field.
Use short bullet rules, not paragraphs. Include: what the product does, who
it's for, the data we store, our domain terms, design guidelines, and a clear
list of NON-GOALS (things we are deliberately not building). Keep it well
under the character limit and easy for a non-technical founder to maintain.
```

**Set up repo documentation and an instruction file:**

```
SCOPE: documentation and agent-instruction files only. Do not change any
product behaviour.

1) Create a root-level AGENTS.md that states the rules you should always
   follow when working on this project: keep the architecture simple and
   robust, follow our design system, don't change unrelated files, don't
   restructure the database without asking, and verify changes in the
   browser before marking them done.
2) Create a /docs folder with a short README describing what the product is,
   the main screens, and our data model.
Show me the plan first and wait for my approval before creating anything.
```

**Define negative guardrails (the "do not" list):**

```
Add a "Guardrails — do not do" section to our workspace knowledge. Include:
do not introduce new libraries or dependencies without flagging them first;
do not change files outside the stated scope of a request; do not remove or
rename database fields without explicit approval; never put secrets, keys, or
personal data in client-side code or logs; no placeholder/lorem-ipsum copy.
Keep each as a short, direct rule.
```

> For the current detail on how knowledge, skills, and instruction files work, see Lovable's own documentation at [docs.lovable.dev](https://docs.lovable.dev/features/knowledge). It changes as the product evolves.

---

## You leave with

- AI-based planning skills and practical techniques
- a finished **PRD**
- a working **prototype**
- a set of **concrete next steps**

---

*Part of the AI-Native Business Design workbook · [Mindset](01-mindset.md) · [Planning](02-planning.md) · By Tommi Järvinen — tommi@firstkiss.co*
