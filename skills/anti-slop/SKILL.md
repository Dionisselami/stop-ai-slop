---
name: anti-slop
description: "The finish gate for anything an AI writes or builds: catch slop in prose, UI, code and docs before it ships. Use when drafting or reviewing marketing copy, docs, READMEs, blog posts, UI screens, components, or code an agent produced; when a deliverable feels generic, padded, or confidently empty; or when someone says 'this reads like AI', 'stop the slop', 'run the slop gate', 'is this good enough to ship', or asks for a pre-ship review. Provides the tells, the fixes, and a hard checklist that must pass before you call the work done."
license: MIT
metadata:
  version: "1.0.0"
  author: "Dionis S."
  tags: "anti-slop, quality, editing, ui, prose, code-review, finish-gate"
  compatibility: "Any agent that can read project files. No tools, services or accounts required."
---

# The Slop Gate

Slop is not bad grammar. It is output that looks finished and says nothing: the median of
everything the model has read, delivered confidently, with the seams hidden. It is cheap to
produce, expensive to trust, and it fails the same way every time.

Run this gate before you say a piece of work is done. It applies to four surfaces — prose,
UI, code, docs — and each has its own tells. Read the one you are shipping; the gate at the
end applies to all of them.

**The one question that catches most of it:** *could this have been produced without reading
the specific material in front of me?* If yes, it is slop, whatever its quality.

## Prose

**Tells.** "In today's fast-paced world." "It's not just X, it's Y." Triads everywhere ("fast,
simple, and reliable"). "Delve", "tapestry", "testament to", "landscape", "realm", "unlock",
"elevate", "seamless". A paragraph that restates the heading. Three sentences where one would
do, and the shortest one is the last. Every claim hedged and every hedge contradicted two
lines later. Em-dashes used as a rhythm substitute rather than punctuation.

**Fixes.**
- Delete the first sentence of every section; if the section still makes sense, it was a
  runway, not content.
- Replace every abstraction with the concrete thing it stands for: not "improve the
  experience" but "the form stops asking for the card twice".
- One idea per paragraph, and the idea in the first clause.
- Keep the numbers you actually measured, drop the ones you did not.
- If a sentence could sit in any other product's copy unchanged, cut it or make it about
  this product.

## UI

**Tells.** Hero plus three feature cards plus a testimonial nobody gave. Gradient text on a
dark background because that is what the reference did. Emoji as icons. Real product states
missing entirely: no empty, no loading, no error, no long content, no narrow viewport.
Placeholder names ("John Doe", "Acme Inc") shipped as data. Spacing that is even everywhere,
so nothing is more important than anything else.

**Fixes.**
- Name the user's actual task in the first viewport, in their words, not the category's.
- Design the four states before the happy path: empty, loading, error, overflowing.
- Use real content from the project — real names, real numbers, real long strings — and check
  the narrow width with them in place.
- One element must win the hierarchy. If two things are the same size, neither is.
- Tokens over raw values; if the project has a design system, extend it rather than inventing
  a parallel one.
- Render it and look at it. A page you have not seen is not verified, and a passing build is
  not a looked-at page.

## Code

**Tells.** Functions named `handleData` or `processItems`. Comments that narrate the line
below (`// loop through users`). Abstraction added for a single caller. Try/except that
swallows the error and returns a default. Tests that assert the mock. Dead parameters kept
"for compatibility". A README section explaining what the code obviously does and silence
about the one non-obvious decision.

**Fixes.**
- Name things for what they hold or do, at the level the caller thinks in.
- Delete a comment that repeats the code; add one where the code is surprising.
- Inline an abstraction until there are three real callers.
- Make failure loud at the boundary and handled where it can be acted on.
- Test the behaviour the user would notice, not the shape of the implementation.
- Leave the non-obvious decision as a sentence next to the code, with the reason.

## Docs

**Tells.** "Introduction", "Overview", "Conclusion" as headings. A getting-started section
that installs the library and never shows it doing anything. Feature lists with no ordering.
Screenshots from a version that no longer exists. "Simply", "just", "easily" in front of
anything that is not simple.

**Fixes.**
- Open with the smallest complete thing that works, end to end, in one block.
- Order by what the reader needs next, not by how the code is organised.
- Replace adjectives with the constraint that produces them ("fast" → "answers in 200 ms on
  the smallest box we run").
- Every claim gets checked against the current build, or it gets removed.

## The gate

Before you claim the work is done, answer these in one line each. A "no" is not a reason to
lower the bar; it is the remaining work.

1. **Specific** — does every sentence, screen and function refer to this project's actual
   material rather than the category's?
2. **States** — for UI: empty, loading, error, overflow, narrow width, seen rendered. For
   prose and docs: the exceptions, limits and failure cases named.
3. **Claims** — is every number, price, comparison and capability checkable, and checked?
4. **Cut** — was at least a fifth of the first draft deleted? If nothing was removed, nothing
   was decided.
5. **Own** — could a competitor ship this unchanged? If yes, it is not done.
6. **Honest limits** — is anything you could not verify stated as unverified rather than
   implied as proven?

Report the result in the handoff: what changed, what you actually tested, and what remains
uncertain. Do not describe the process; show the artifact.

## Companions

- **Prose at length** (books, long-form): the `anti-prose-slop` skill in this repo, which
  pairs a genre recipe with a corpus of model passages and a self-edit pass.
- **Prose mechanics**: the `humanizer` skill in this repo — a catalogue of AI writing
  patterns with rewrites (MIT, by Siqi Chen).
- **UI evidence**: UIZZE's `anti-ui-slop` skill (Apache-2.0, by UIZZE) grounds UI decisions in
  real web and iOS screens and adds a design contract plus a finish gate. It is deliberately
  **not vendored here** — its LICENSE, NOTICE and MODIFICATIONS must travel with it, and it is
  authored by someone else. Get it from UIZZE (uizze.com) and install it from their own
  distribution. The UI section above is self-contained without it; it just lacks the reference
  library.
