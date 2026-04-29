# Brain Dump Template (EN)

A raw record of a long message from the friend. Captured verbatim before processing.

## When to create one

The friend sends a message ≥ ~200 words that's a thought stream — multiple ideas,
requirements, or context dumped together. You recognize it as more than a simple
instruction.

## Frontmatter

```yaml
---
type: brain-dump
date: YYYY-MM-DD
topic: <2-4 word slug>
processed: false
tags: [...]
---
```

## Body structure

1. **Raw transcript** — paste the friend's message verbatim. Do not edit, summarize,
   or reflow.
2. **(After processing)** A "Processed" section listing the entities extracted, links
   to the entity files created/updated, and a one-paragraph synthesis.

## Filename

`agy/brain-dumps/YYYY-MM-DD-<topic-slug>.md`

## Example

```markdown
---
type: brain-dump
date: 2026-04-29
topic: q3-strategy
processed: false
tags: [strategy, work]
---

# Q3 Strategy Brain Dump

So I've been thinking about Q3 and there are three things on my mind...
[verbatim continues]
```
