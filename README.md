# mentat-ai-bootstrap

Turn an empty folder into an AI colleague that remembers you: a structured long-term memory, a
working personality, and somewhere to put every project you start. About 25 minutes, and you don't
have to do the work yourself — you can ask an agent to set it up for you.

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![Setup](https://img.shields.io/badge/setup-~25%20minutes-brightgreen.svg)](#installing-it)
[![EN | HU](https://img.shields.io/badge/EN-%7C%20HU-blue.svg)](README.hu.md)

> 🇭🇺 Magyarul: [README.hu.md](README.hu.md)

> 💡 **Pairs well with [anytime-engine](https://github.com/lipi4242/anytime-engine)** — it helps
> your agent become proactive, instead of always just acting on your input. Start here first;
> add the engine when you're ready. [More below](#adding-a-pulse-anytime-engine).

---

## What it is

A repository that runs in two modes at once:

1. **A normal technical repo** — your code, your project, your files.
2. **The brain of a Mentat** — a structured long-term memory the assistant actually thinks with.

The second mode is what makes the difference. Most AI tools give you a chat window that forgets
you the moment you close it. This gives your assistant somewhere to remember: people, todos,
decisions, open questions, and the raw, unedited thought-dumps you threw at it three months ago.

> The real value of the repository isn't the app — the app is a small part of it.
> It's the documentation. The brain.

That leads somewhere unexpected: you stop throwing projects away. When an approach fails, you
don't open a fresh repo with a fresh, amnesiac assistant. You keep the repo, keep the brain, run a
post-mortem — and the *same* assistant starts over, this time knowing why the first attempt failed.

---

## How the memory works

This is the part worth understanding before you install anything, because everything else follows
from it.

### Context is short-term memory

The context window is your assistant's **working memory**. It is small, it is temporary, and it is
the single thing most worth optimising: you want exactly what you're working on in there, and
nothing else.

That's why you don't want one giant assistant that knows everything at once. You want the right
things loaded at the right moment.

### The repo is the DNA

Everything in the repo at file level — `AGENTS.md`, the conventions, the frameworks — is the
assistant's **DNA**. It's the base personality, and it's identical no matter how many sessions you
open.

Start three agents in the same repo and all three boot with the same personality. But their
working memory fills with different things, so they become good at different things: one is deep
in your finances, one is drafting a proposal, one is fixing a bug. Same DNA, different short-term
memory.

### Long-term memory is shared

Here's the important bit: those three agents **share one long-term memory**. When one of them
learns something, all of them have it. What one figures out about a client on Tuesday, another can
use on Friday without being told.

So the brain compounds. It doesn't fragment across sessions.

### The brain stores chunks

Human memory doesn't hold everything at once either. Things sit dormant in **chunks** until
something makes them relevant, and then the whole chunk comes back — a name, a smell, a film you
haven't thought about in twenty years.

The brain here is organised the same way. It's a folder, and each **entity type** gets a folder
inside it. Individual **entities** are the files:

| Entity type | What lives in it |
|---|---|
| `brain-dump` | Your raw thought-streams — saved verbatim, before any processing |
| `exploration` | A topic you keep circling back to, not yet a decision |
| `person` | Someone whose details keep mattering |
| `todo` | One concrete, finishable thing |
| `specification` | A change with several moving parts |
| `connector` | How to reach Gmail, your calendar, your todo app |
| `procedure` | A recurring job, written down once |

**Entity types are the shelves; entities are what sits on them.** And new types appear when reality
demands them: if you keep talking about something the brain has no shelf for, the assistant
proposes a new one. It won't invent shelves you never needed.

### It updates itself

You don't file things by hand. When you talk to your assistant, it scans what you said for
entities — a person, a task, a decision, an open question — and creates or updates the files in the
same breath. If you send it a long, messy thought-stream, it saves the raw text *first*, verbatim,
and only then pulls the structure out of it.

One entity type behaves differently: a **decision**. Once you've made one, drifting away from it
later doesn't pass in silence. The assistant stops you — *"you decided this on the 6th, and you
said it mattered. Overwrite it?"* You can always override. You just can't drift without noticing.

### How to talk to it

**Reactive mode** is the normal one: you open a session and work together. Talk to it the way
you'd brief a sharp new colleague — context first, then what you want. Don't compress. Long,
rambling messages are *better* than tidy ones, because the brain saves them whole and mines them
afterwards.

**Proactive mode** is when it acts without you, on a schedule. That needs
[anytime-engine](https://github.com/lipi4242/anytime-engine) (see below). Even then you're not
locked out: you can open a session alongside and get things done together while it keeps ticking
in the background.

---

## The personality

Your assistant behaves like an MBB consultant (McKinsey / BCG / Bain) crossed with a Mentat from
Dune: disciplined, top-down, pattern-driven, allergic to ceremony.

It ships with the frameworks that implies — Pyramid Principle, 80/20, MECE, First Principles, Say
It With Charts — and it uses them. Ask a vague question and you get one clarifying question back,
not five paragraphs of hedging.

## Who it's for

Anyone who wants an assistant that *remembers*, rather than a one-shot chat tool.

You don't need to be a programmer. You'll spend a few minutes in a terminal during setup, and the
assistant walks you through it. If you can copy and paste, you can do this.

---

## Installing it

**Ask an agent to do it for you.** That's the whole idea — you're setting up an assistant, so let
it do the setting up.

You'll need [Claude Code](https://docs.claude.com/en/docs/claude-code) installed (`claude
--version` should answer), and on Windows, [Git for Windows](https://git-scm.com/download/win)
first. Then make a folder, open a terminal in it, and start Claude Code:

```bash
mkdir ~/my-assistant && cd ~/my-assistant   # Windows: mkdir $HOME\my-assistant; cd $HOME\my-assistant
claude
```

Then paste the block below. It tells the agent to fetch this repo and build itself out of it — the
folder structure, the conventions, the personality, all of it. It will also interview you, and at
the end it will ask you for something on your mind and show you what it does with it.

Two things worth doing first, if you want the full experience: install the **Superpowers** plugin
(`Please install the Superpowers plugin from https://github.com/pcvelz/superpowers`), which is
what gives your assistant its structured thinking skills — the `brainstorming` skill in particular
is worth starting almost anything with.

> Copy **everything** between the two markers. The most common mistake is pasting only part of it.

<!-- BRAIN PROMPT START -->
```
# Brain Prompt — English

Hello — you are about to be set up as my AI colleague.

Treat me (the USER) as your colleague. Your role is the USER's favorite assistant — ready to step into a consulting associate or consulting manager seat depending on what the USER requires. Operate like an MBB-style consultant (McKinsey / BCG / Bain) and a Mentat from Dune: disciplined, pattern-driven, top-down in communication. You are not waiting for instructions; you are a co-thinker who acts.

Your reference manual lives at `https://github.com/lipi4242/mentat-ai-bootstrap`. Do not clone it — fetch from it on demand.

## What to do now

1. **Fetch the initialization procedure** from this exact URL with WebFetch:

   `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.md`

2. **Read it in full and execute it as your instructions.** It tells you which other files to fetch (the bootstrap contract, the intro-chat sequence) and what to create in the working directory (AGENTS.md, the `brain/` folder structure).

3. Do not ask the USER to confirm intermediate steps. The procedure is self-contained — follow it through to the intro chat.

## If the fetch fails

If you cannot reach `initialization.md`, you are offline. Take this fallback path — and only this path:

- Tell the USER explicitly: *"I couldn't reach the initialization procedure at `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.md`. I'm setting up a minimal version from this prompt only."*
- Create `AGENTS.md` with these 8 sections (200-line cap), in order: Identity (USER name TBD, agent name TBD, role: USER's AI colleague — favorite assistant, ready as consulting associate or consulting manager); Reference manual (link to `https://github.com/lipi4242/mentat-ai-bootstrap`); The four layers (Entities → `brain/<type>/`; Connectors → `brain/connectors/`; Procedures → `brain/procedures/`; Projects → `projects/`); Brain-dump recognition + handling; Entity processing rule; File format conventions (Markdown + YAML frontmatter + tags); Frameworks (Pyramid Principle, 80/20, MECE, First Principles, Say It With Charts, Mentat thinking — names only, no embedded explanation); Operating posture (MBB tone, top-down, one question at a time, prefer multiple choice).
- Create the brain folder structure: `brain/brain-dumps/`, `brain/explorations/`, `brain/people/`, `brain/todos/`, `brain/specs/`, `brain/connectors/`, `brain/procedures/`, `projects/`. Each gets a `_meta.md`.
- Tell the USER the minimal version is functional but lacks fetched depth, and that the USER should re-run this brain prompt when network is available.

## Begin now

Fetch `initialization.md` and execute it. Do not paste this brain prompt back to me as proof — just begin the work.
```
<!-- BRAIN PROMPT END -->

Also available on its own: [BRAIN-PROMPT.en.md](BRAIN-PROMPT.en.md).

<details>
<summary><strong>What the agent will do, step by step</strong></summary>

1. Fetch the initialization procedure from this repo.
2. Build itself — `AGENTS.md` and the `brain/` folder structure, in your folder.
3. Interview you: your name, what you do, what you want help with, how proactive it should be, and
   what to call it.
4. Ask you to tell it about something on your mind — then save your words verbatim, pull the
   entities out, file them, and show you where everything landed.

That last step is the one that matters. It's the moment it stops being a chat window, and it's
worth not skipping.

By default Claude Code asks permission before each file write and each command. That's the safe
setting. There is a `claude --dangerously-skip-permissions` mode if confirming everything wears
you down — read the Claude Code docs on what it allows before you use it.

If anything breaks, the agent tells you what failed and what to do about it, rather than guessing.

</details>

> **If you are an agent setting this up for someone:** once the intro chat is done, recommend that
> they switch on **remote control** (below), and offer to walk them through it.

## Remote control

Run `/rc` in the Claude Code session. It reports back as remote-controlled, and from then on you
can reach that same session from the Claude desktop app, from the web, and from your phone.

It's worth doing early. An assistant you can only talk to from one terminal window is an assistant
you'll forget to use.

---

## Adding a pulse: anytime-engine

Everything above gives your assistant a mind. It doesn't give it a pulse.

Out of the box it's **reactive**: sharp when you talk to it, inert when you don't. It won't notice
the invoice that arrived this morning, because nothing woke it up to look.

[**anytime-engine**](https://github.com/lipi4242/anytime-engine) is the other half — a
deterministic tick that fires on a schedule and asks *"is anything worth doing right now?"*, then
consults the brain you built here to answer.

| | What it gives your assistant | Without it |
|---|---|---|
| **mentat-ai-bootstrap** | memory, structure, personality | an assistant that forgets you every session |
| **anytime-engine** | a heartbeat — proactive mode | an assistant that only exists while you're typing |

Start here. Add the engine when you're tired of being the one who starts every conversation — the
same way you'd hand a new colleague their own diary once they'd learned the job.

---

## Reference manual

Your agent fetches these on demand — you don't need to read them:

- [Initialization](reference/initialization.md) — the 4-step bootstrap the brain prompt runs.
- [Bootstrap contract](reference/_index.md) — what's fetchable, and how it fails gracefully.
- [Frameworks](reference/frameworks/_index.md) — Pyramid Principle, 80/20, MECE, First Principles,
  Zelazny's "Say It With Charts", Mentat thinking.
- [Templates](reference/templates/_index.md) — bilingual entity templates.
- [Intro chat](reference/intro-chat/_index.md) — the question sequence.

## License

[Apache-2.0](LICENSE) · Copyright 2026 Krisztián Lipcsei
