# TrackPlay docs: voice and format

Not published (Mintlify only builds pages listed in `docs.json`). This is the
standard every `.mdx` in this repo is held to.

## The voice

Distilled from trackplay.io. The product has a point of view: *"every feature answers one
question. Does this move a viewer closer to buying?"* The docs must sound like the same
company, not like a manual bolted onto it.

**Short declarative sentences. Second person. Concrete over abstract.**

> Your host counts plays. This one counts buyers.
> Your pixel fires on page load. Which means you are retargeting people who
> bounced at second three.
> Fire it at the 75% mark instead, when intent is real.

### Punctuation: the two hard rules

These are not preferences. The marketing site contains **zero** of each, and the docs must
match it.

**1. No em-dashes. No en-dashes. Ever.**

The brand voice makes its point by stopping and starting again. A dash softens a sentence
that is supposed to land. Use one of these instead:

| Instead of a dash | Use |
| --- | --- |
| Joining two related statements | A full stop. Two sentences. |
| Drawing a contrast | The contrast comma: `Fire your pixel at 75%, not on page load.` |
| Introducing a list or an explanation | A colon. |
| An aside | Parentheses, or cut the aside. |

> Your host counts plays. This one counts buyers.
> Winner picked on real sales, not click-through.
> No developer. No plugins. One embed.

**2. No contractions.** Spell the negation out. `cannot`, `does not`, `do not`,
`will not`, `is not`, `it is`, `you are`. Possessives are fine (`your plan's limit`).

> It cannot tell you which one of them bought.
> Six things your current host does not do.
> We do not hold your attribution data hostage.

Spelling it out is what makes the voice sound certain rather than chatty. `It can't` is a
shrug. `It cannot` is a verdict.

### Rules

1. **Lead with what it does for them, not what it is.**
   - No: "The Custom Events API is a powerful server-to-server ingest endpoint."
   - Yes: "Send TrackPlay an event the player never saw (a lead form, a quiz completion,
     an upsell). It lands on the same session as the play."

2. **Banned words.** `comprehensive`, `powerful`, `seamless`, `robust`,
   `effortless`, `leverage`, `utilize`, `simply`, `just`, `easy`, `unlock`,
   `elevate`, `supercharge`, `world-class`, `cutting-edge`. If a sentence needs an
   adjective to be impressive, the sentence is weak. Delete the adjective.

3. **Never say "simply" or "just".** They tell a stuck reader the thing they cannot
   do is trivial. Removing them costs nothing and never insults anyone.

4. **Name the failure, not just the happy path.** The marketing voice is built on
   contrast ("it can tell you X, it cannot tell you Y"). Docs inherit that: say what
   goes wrong, what the error code is, and what to do about it.

5. **Concrete numbers over vague ranges.** "600 requests per minute per workspace",
   not "generous rate limits". If a limit is configurable, give the default *and*
   the env var.

6. **No filler openers.** Delete "In this guide, we will...", "Welcome to...",
   "This section covers...". Start with the first useful sentence.

7. **Truthful about limits.** The about page promises "raw, auditable events...
   no vanity metrics, no black-box score". Docs must say when something is
   at-least-once, when a retry can double count, when a value is an estimate.
   Never oversell reliability.

8. **One embed, no developer.** Where a task genuinely needs no code, say so. Where
   it genuinely needs code, do not pretend otherwise.

## Mintlify format

Every page uses the component set. Prose-only pages are a bug.

| Situation | Component |
|---|---|
| Sequential setup | `<Steps>` / `<Step title="…">` |
| Landing / index pages | `<CardGroup cols={2}>` / `<Card icon="…" href="…">` |
| Per-platform or per-language variants | `<Tabs>` / `<Tab title="…">` |
| Same call in curl / JS / PHP | `<CodeGroup>` |
| Request parameters | `<ParamField body="…" type="…" required>` |
| Response fields | `<ResponseField name="…" type="…">` |
| Nested object fields | `<Expandable title="…">` |
| FAQs, error-code tables, edge cases | `<AccordionGroup>` / `<Accordion>` |
| Aside the reader may skip | `<Note>` |
| Something that will cost them money or data | `<Warning>` |
| A non-obvious shortcut | `<Tip>` |

### Frontmatter

Every page:

```yaml
---
title: "Custom Events API"
description: "Send an event that happened outside the player and land it on the viewer's session."
icon: "bolt"
---
```

`description` is the search snippet and the social preview. Write it as a real
sentence in the voice above. Never "Documentation for the custom events API."

### API pages

API reference pages are generated from `api-reference/openapi.json`, so the
playground works and the schema cannot drift from the docs. Hand-written prose
belongs in a guide page that *links* to the reference, not in a second, stale copy of the
schema.

### Code samples

- Real, runnable, copy-pasteable. No `<your-value-here>` where a real example works.
- Show the response too, including the error response.
- Placeholder token is always `tplt_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`.
- Base URLs: `https://app.trackplay.io` (app API), `https://e.trackplay.io` (events).
