# mentat-ai-bootstrap

Set up your own personal AI colleague using Claude Code + the Superpowers plugin. EN/HU.

> Magyarul: [README.hu.md](README.hu.md)

## What this is

A bootstrap kit. After ~25 minutes of guided setup, you'll have a working AI colleague that:
- Recognizes long messages as "brain dumps" and saves them verbatim before processing.
- Tracks people, todos, explorations, specifications, connectors, procedures, and projects as structured Markdown files.
- Communicates in MBB-consultant style (top-down, Pyramid Principle, MECE) and thinks like a Mentat from Dune.
- Starts as a vocabulary-and-shape installation; real integrations (Gmail, TickTick, etc.) get wired up later when you ask.

## Who this is for

Anyone who wants a personal AI assistant that *remembers* — not a one-shot chat tool. You don't need to be technical, but you'll be in a terminal for the install.

## Install steps

### 1. Install Claude Code CLI

- **macOS:** Follow https://docs.claude.com/en/docs/claude-code (Homebrew or installer). Open Terminal (Cmd+Space → "Terminal") or iTerm to verify: `claude --version`.
- **Windows:** Install Git for Windows first (https://git-scm.com/download/win), then follow the Claude Code Windows install guide. Open PowerShell (Start menu → "PowerShell") to verify: `claude --version`.

### 2. Make a folder for your assistant + open a terminal there

- **macOS (Terminal or iTerm):**
  ```
  mkdir ~/my-assistant && cd ~/my-assistant
  ```
- **Windows (PowerShell):**
  ```
  mkdir $HOME\my-assistant; cd $HOME\my-assistant
  ```

You can name the folder whatever you want — `my-assistant` is just an example.

### 3. Start Claude Code

```
claude
```

Claude will ask for permission before each file write or shell command. Confirm each one — this is the safe default.

> **Advanced (use at your own risk):** if you get fed up with confirming every action, there is an alternative launch:
> ```
> claude --dangerously-skip-permissions
> ```
> This grants Claude broad access to your system, including the ability to run shell commands without your explicit approval. **Read the Claude Code documentation** about what this enables before using it. Only use it if you understand and accept the risks.

### 4. Install the Superpowers plugin

In the Claude Code prompt, type:

```
Please install the Superpowers plugin from https://github.com/pcvelz/superpowers
```

Wait for installation to complete (typically under a minute).

### 5. Paste the brain prompt below

Copy the entire block below (everything between the `<!-- BRAIN PROMPT START -->` and `<!-- BRAIN PROMPT END -->` markers) and paste it into the Claude Code prompt. Then hit enter.

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

## What happens next

Your agent will:
1. Fetch the initialization procedure from this repo.
2. Create `AGENTS.md` and the `brain/` folder structure in your folder.
3. Start an intro chat — your name, what you do, what you want help with, agent personality, and finally a brain-dump demo where you tell it about something you're thinking about and it processes it end-to-end. That's the activation moment.

If anything fails, your agent will tell you exactly what failed and what to do.

## The brain prompt as a standalone file

Same content as embedded above: [BRAIN-PROMPT.en.md](BRAIN-PROMPT.en.md).

## Reference manual

Your agent fetches deeper detail on demand from `reference/`:
- [Initialization](reference/initialization.md) — the 4-step bootstrap procedure the brain prompt directs the agent to.
- [Bootstrap contract](reference/_index.md) — what's fetchable and how.
- [Frameworks](reference/frameworks/_index.md) — Pyramid Principle, 80/20, MECE, First Principles, Zelazny "Say It With Charts", Mentat thinking.
- [Templates](reference/templates/_index.md) — bilingual entity templates.
- [Intro chat](reference/intro-chat/_index.md) — the question sequence.
