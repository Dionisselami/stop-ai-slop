# Stop AI slop

**Three skills that catch the same failure in different clothes: output that looks finished and
says nothing.**

Slop is the median of everything a model has read, delivered confidently. It is not a style
problem — it is a *specificity* problem, and it fails the same way every time. This repo is the
gate you run before calling work done.

```
npx skills add Dionisselami/stop-ai-slop -y
```

Installs all three. To take one:

```
npx skills add Dionisselami/stop-ai-slop --skill anti-slop -y
```

## What's inside

| Skill | Surface | What it does |
|---|---|---|
| **`anti-slop`** | All four | The finish gate. Tells, fixes and a six-question checklist for prose, UI, code and docs. Start here. |
| **`anti-prose-slop`** | Long-form prose | For books and long documents: pick a genre recipe, read model passages before drafting, then run a self-edit pass before declaring done. Pairs with the Proseify MCP server. |
| **`humanizer`** | Prose mechanics | A catalogue of AI writing patterns with rewrites — the specific tells and their fixes (MIT, by Siqi Chen). |

## When to use which

- Anything about to ship, from any agent → **`anti-slop`**. It routes to the others.
- Writing fiction or a long document → **`anti-prose-slop`**.
- Editing a paragraph that "reads like AI" → **`humanizer`**.

## The gate, in short

Before claiming done, answer six questions in one line each:

1. **Specific** — does every sentence, screen and function refer to *this* project's material?
2. **States** — are empty, loading, error and overflow designed and seen; are limits and
   exceptions named?
3. **Claims** — is every number, price and capability checkable, and checked?
4. **Cut** — was at least a fifth of the first draft deleted?
5. **Own** — could a competitor ship this unchanged?
6. **Honest limits** — is what you could not verify stated as unverified?

The single test that catches most of it: *could this have been produced without reading the
specific material in front of me?* If yes, it is slop regardless of execution quality.

## Companion, not included

[UIZZE](https://uizze.com)'s `anti-ui-slop` skill (Apache-2.0) grounds UI work in real web and
iOS screens. It is **not vendored here** — it is someone else's work with its own LICENSE,
NOTICE and MODIFICATIONS that must travel with it. Install it from UIZZE's own distribution.
The UI section of `anti-slop` works without it.

## Licence

MIT for the skills in this repo (see `LICENSE`). `skills/humanizer/` keeps its own MIT licence
and author. Full attribution in `NOTICE`.
