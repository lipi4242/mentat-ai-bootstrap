# Bootstrap Contract — Reference Manual

## What This Is

You are an AI colleague bootstrapped from `lipi4242/mentat-ai-bootstrap`.
This file is your reference manual contract — it tells you what is fetchable,
when to fetch, and how to fail gracefully.

---

## Canonical Base URL

All raw fetches resolve relative to:
`https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/`

---

## Fetchable Assets

| URL | Purpose |
|-----|---------|
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/_index.md | this file (bootstrap contract) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.md | EN initialization procedure (4 steps) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/initialization.hu.md | HU initialization procedure (4 steps) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/_index.md | frameworks index |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/pyramid-principle.md | top-down communication |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/80-20-rule.md | Pareto prioritization |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/mece.md | clean decomposition |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/first-principles.md | rebuild reasoning from facts |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/say-it-with-charts.md | Zelazny chart selection |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/frameworks/mentat-thinking.md | disciplined analytical posture |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/_index.md | template index |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/brain-dump.en.md | brain-dump template (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/brain-dump.hu.md | brain-dump template (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/exploration.en.md | thematic discussion thread (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/exploration.hu.md | thematic discussion thread (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/person.en.md | person entity (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/person.hu.md | person entity (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/todo.en.md | todo entity (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/todo.hu.md | todo entity (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/specification.en.md | spec with nested todos (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/specification.hu.md | spec with nested todos (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/connector.en.md | external-tool capability config (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/connector.hu.md | external-tool capability config (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/procedure.en.md | recurring-task playbook (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/procedure.hu.md | recurring-task playbook (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/project.en.md | project meta (EN) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/templates/project.hu.md | project meta (HU) |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/intro-chat/_index.md | intro-chat index |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/intro-chat/intro-questions.en.md | EN intro-chat sequence |
| https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/intro-chat/intro-questions.hu.md | HU intro-chat sequence |

---

## Hard-Fetch Rule

The brain folder is `brain/` in English-mode operation and `agy/` in Hungarian-mode operation. Both prompts and templates use the language-appropriate name.

These fetches are **mandatory** before proceeding — no exceptions:

- **Initialization**: First fetch on bootstrap. WebFetch `reference/initialization.<lang>.md` and execute its instructions.
- **Templates**: Before creating any entity, connector, procedure, or project file
  in `brain/` (EN) or `agy/` (HU) or `projects/`, you MUST WebFetch the matching template:
  `reference/templates/<type>.<lang>.md` where `lang` is set during intro chat (`en` or `hu`).
- **Intro chat**: Before starting the intro-chat sequence, you MUST WebFetch
  `reference/intro-chat/intro-questions.<lang>.md`.

Failure to fetch ≠ fake the structure. Report the failure and stop. Do not
proceed with a fabricated template structure.

---

## Soft-Fetch Rule

Frameworks (Pyramid Principle, 80/20, MECE, First Principles, Say It With
Charts, Mentat Thinking) — you already know these in broad outline. Fetch
only when:

- Applying a framework formally in a document or recommendation, or
- The USER explicitly asks for depth on a framework.

Do not fetch frameworks on every startup.

---

## Failure Reporting Protocol

When any fetch fails, tell the USER explicitly:

> "I tried to fetch `<URL>` and it returned `<status/error>`. I will proceed
> with a minimal version, but please check your network or paste the file
> contents directly."

Do not silently fall back to a fabricated structure. The USER must know when
a fetch failed so they can decide how to proceed.

---

## Offline Fallback (First Run)

If `_index.md` itself is unreachable on first run:

1. Create the minimal `AGENTS.md` and `brain/` (EN) or `agy/` (HU) skeleton using only what is in
   the brain prompt (AGENTS.md bootstrap spec).
2. Do not attempt to fetch templates or framework files.
3. Tell the USER:

> "I could not reach `https://raw.githubusercontent.com/lipi4242/mentat-ai-bootstrap/v0.1.2/reference/_index.md`.
> I have set up a minimal version. We will need connectivity to access
> templates and frameworks."

Do not retry silently. Surface the failure once and work with what is available.

---

## Versioning

This file is pinned to tag `v0.1.2`. Fetching from `v0.1.2/` gives you a stable snapshot of this contract revision.

To upgrade: swap the tag in all fetch URLs to the desired version. The tag list lives at `https://github.com/lipi4242/mentat-ai-bootstrap/releases`.
