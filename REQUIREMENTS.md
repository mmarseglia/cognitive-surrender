# REQUIREMENTS — Cognitive Surrender Publication

*Specification for the publication in this repository. Date: 2026-04-22.
Status: draft.*

This document specifies what the publication must contain, who it must
serve, and what behavior it must produce. It is the contract the draft
will be measured against. The publication lives in `README.md` (the
persuasion layer) and `prompts/` (the reference layer). The source
material it was drafted from is not kept in this repository.

---

## Purpose

Specify what the publication must contain and do. The publication's single job is to move a reader from
encountering the idea of *cognitive surrender* to installing one of the
prompts in the reference layer, and — for a reader who is already
convinced — to forward the publication to peers.

---

## Reader personas

The publication serves two readers whose paths through it diverge, but
whose target action is the same (install at least one prompt). Every
requirement below must be checked against both.

**Reader A — the motivation-gap software engineer.**
Uses AI coding tools daily — Copilot, Cursor, Claude Code, ChatGPT for
debugging. Comfortable with hallucinated function signatures and has
caught them before. Prevailing belief: *"I use AI for leverage, but I
review its output. I'm not one of the people being fooled."* Has never
heard of *cognitive surrender*. Arrives only because a peer forwarded the
link. Will abandon within ~200 words if the opening reads as another
"AI is making us dumber" take.

**Reader B — the ammunition-gap software engineer.**
Already worried about AI coding tools, especially for juniors who never
built the underlying skill. Reads HN and Lobste.rs. Lacks the citable
study, the precise vocabulary (*cognitive surrender*, *supernormal
releaser*, *tri-system*), and the deployable assets to make the case in
PR reviews, Slack threads, or onboarding docs. Seeking a briefing to use
and share.

**Scope.** Both readers are assumed to be Claude users, or willing to
become Claude users. Readers who exclusively use other assistants
(ChatGPT, Gemini, local models) are out of scope; the prompts rely on
Claude-specific surfaces (Settings → Personalization, Projects).

---

## Success criteria

**Outcome criteria** (target behavior; measurable in principle via direct
feedback or analytics):

1. Reader A installs at least one prompt within a week of first read.
2. Reader B installs at least one prompt *and* forwards the canonical
   link to at least two peers within a week.

**Design heuristics** (tests the author applies to drafts, not the
reader):

3. A reader asked a week later can state the core Shaw & Nave finding in
   a single sentence in their own words. If the draft does not foreground
   the finding clearly enough to pass this test, the draft fails.
4. Comprehension without action counts as failure. If a draft reads as
   satisfying *on its own*, with no pull toward the prompts, it fails.

---

## Structural rules

The publication is organized as two sequenced layers. These rules govern
the shape before any content requirement:

1. **Two-layer rule.** Persuasion layer first, reference layer second.
   No interleaving — prompts do not appear inside the persuasion layer.
2. **Independence rule.** Each layer is useful on its own. A Reader B
   who skips the persuasion layer must still get everything they need
   from the reference layer. A Reader A who never reaches the reference
   layer must still have received something worth the read.
3. **Transition rule.** A single, explicit, signposted handoff separates
   the layers. Reader B uses it to skip ahead; Reader A uses it to pace
   the shift from "why" to "how."
4. **Time-to-value constraints.**
   - Reader A reaches the transition in under about four minutes of
     reading (roughly 800–1000 words for §§1–4 combined).
   - Reader B reaches the first copy-pasteable prompt within one click
     of arriving at the reference layer. The landing page
     (`prompts/README.md`) shows the selection aid and a link to every
     prompt without scrolling, and each prompt file shows its code
     block without scrolling (both measured on a 1440×900 desktop
     viewport).

---

## Section-by-section content requirements

Each numbered item is a constraint on a section of the publication.
Names are illustrative; the author may rename sections, but the required
content must land somewhere.

### Persuasion layer

**§1. Opening.** Within the first 200 words, must land (a) a specific
engineering-surrender image the reader recognizes — accepting a Copilot
autocomplete of a function that doesn't exist, merging an AI-suggested
refactor without tracing the diff, nodding through a PR review generated
by an AI tool — before (b) pivoting to the Shaw & Nave finding. Must
distinguish *cognitive offloading* (using a linter, using a code
formatter) from *cognitive surrender* (adopting the AI's output as your
own thinking). Must name researchers (Shaw, Nave), institution (Wharton),
and the headline result: participants adopted AI answers even when those
answers were wrong, with confidence rising ~10% regardless of correctness.

Must not open with generic AI-doomer rhetoric, an unsourced anecdote, or
a personal hook that delays the finding.

**§2. The study.** Present the Cognitive Reflection Test experiment with
enough detail to be cite-able: manipulated ChatGPT answers, ~50% control
accuracy, performance falling *below* baseline when the AI was wrong.
Keep short — this is evidence, not a literature review.

**§3. Why this happens.** Present the *supernormal-releaser / agentic
pareidolia* reframe. Must be attributed to McRaney as distinct from the
Shaw & Nave study itself. This is the load-bearing section that converts
Reader A from "AI is a neutral tool I use" to "AI acts on evolved
machinery I cannot willpower through." A draft that skips the reframe
fails review even if every other section is strong.

One bounded reference to social media's *dark patterns* is permitted
and useful here (or in §1) — as the nearest prior example of interfaces
designed around cognitive vulnerabilities, it gives the reader a foothold
they already recognize. One or two sentences. Do not expand. See
non-goal 3.

**§4. Handoff.** One clearly-marked paragraph that names the shift —
e.g., *"If you want tools rather than argument, skip to [reference
layer]."* The handoff is what makes the independence rule real.

### Reference layer

**§5. The general prompt.** The general prompt, in its own file
(`prompts/general.md`), presented as a single copy-pasteable code
block. Must include Claude installation instructions (Settings →
Personalization). Installation paths for ChatGPT, Gemini, or other
assistants are out of scope.

**§6. The specialized prompts.** The four project prompts (writing,
coding, research, decisions), one file each in `prompts/`. Each must
name its intended use case and be presented for installation as a
Claude Project system prompt. A selection aid must appear on the
landing page (`prompts/README.md`): *"If you write code daily, install
the coding prompt first. If your AI use is mostly outside code, start
with the general prompt."* This neutralizes the selection-gap friction
that would otherwise re-emerge for Reader A after they're convinced.

**§7. Closing attribution.** Lives at the end of `README.md`, as its
§5. A short final section explicitly naming
which claims originated with Shaw & Nave (the CRT study, the
tri-system extension, the confidence-inflation finding), which with
McRaney (the supernormal-releaser reframe, the *agentic pareidolia*
coinage), and which with the author (framings, organizational choices,
commentary, the selection aid). This section is non-negotiable: a
publication about cognitive surrender whose attribution is blurry
discredits itself.

---

## Tone and voice

The publication's subject is AI-shaped rhetoric acting on human
cognition. The publication itself must not read like AI-shaped rhetoric,
or it discredits itself line-by-line. Tone rules here are structural,
not stylistic — a tone violation falsifies the thesis.

1. **No reader-directed flattery.** No framings that praise the reader
   for reading, for asking good questions, or for being the kind of
   person who engages with hard topics. The publication is useful or it
   is not; it does not compliment.

2. **Calibrated claims.** Specific numbers, names, dates, and study
   details carry their source inline. Inferred or speculative claims
   are flagged explicitly (*"a reasonable inference,"* *"not stated
   directly in the paper, but…"*). A reader should be able to tell
   without looking up a source which line is reportage and which is
   commentary.

3. **No AI-pattern prose.** The following patterns are forbidden:
   - Opening qualifiers: *"It's worth noting that…"*, *"It's important
     to understand…"*, *"In this piece, we will…"*
   - Section-end recaps that restate what was just said.
   - Triadic lists with forced parallelism when two items would do.
   - Hooks that flatter the topic (*"This is a fascinating area…"*).
   - Marketing verbs: *empower*, *unlock*, *transform*, *elevate*.
   - Hedged softening that hides a claim: *"it could be argued,"* *"some
     might say."* Either make the claim or drop it.

4. **Register.** Software engineer familiar with AI coding tools.
   Technical terms (hallucinated signatures, agentic coding, tool use,
   context windows, PR review) appear without explanation. Do not pause
   to define what Copilot or Cursor is.

5. **Active voice by default.** Passive voice is permitted where it
   correctly displaces subject (*"participants' confidence rose"*) but
   not as a hedge against ownership (*"mistakes were made"*).

---

## Attribution

Attribution is structural, not decorative. It appears throughout §§1–6
in named form, and formalizes in §7.

1. **Named sources.** Shaw, Nave, Wharton, McRaney, *You Are Not So
   Smart*, and the SSRN working paper are each named in-text on first
   use. No anonymous *"researchers have found"* or *"studies show"*
   formulations.

2. **Voice separation.** Author framings, phrasings, and recommendations
   are visibly distinct from the findings of the cited researchers. When
   the author speaks as themselves — offering commentary, a reframe, or
   a recommendation — they use first person (*"my reading,"* *"I
   think"*) to keep the seam visible.

3. **McRaney's contributions.** *Agentic pareidolia* and the application
   of *supernormal releasers* to LLMs are McRaney's framings, not Shaw
   & Nave's. Named on first use with that attribution.

4. **Shaw & Nave's contributions.** *Cognitive surrender* (as distinct
   from *cognitive offloading*), the CRT experiment design, and the
   *tri-system* extension of Kahneman's dual-process model are Shaw &
   Nave's. Named on first use with that attribution.

5. **Author contributions.** Any organizing framing, recommendation
   (which prompt to try first, how to stack them), engineering-specific
   examples (the Copilot/PR-review images in §1), or original commentary
   originates with the author and is marked as such.

---

## Non-goals

- **Not an exhaustive review of AI cognition research.** The piece
  anchors on the Shaw & Nave paper. If tempted to catalog adjacent
  studies (*"see also…"*), link Shaw & Nave and stop.

- **Not an "AI bashing" piece.** The argument is about the intersection
  of human cognitive biases and AI, not about AI being bad. If a
  paragraph reads as blaming the tool rather than describing what the
  tool exploits in us, rewrite it.

- **Not an excursion into social media's dark patterns.** A single
  reference to dark patterns is permitted and desirable — the nearest
  prior example of UI designed around cognitive vulnerabilities gives
  the reader a foothold. One gesture, then back to the Shaw & Nave
  material. Do not expand.

- **Not about general AI risks.** Existential risk, autonomous-agent
  risk, alignment, labor displacement, and broader AI-ethics discourse
  are all out of scope. The piece is about what happens at the decision
  layer between a human and a running model.

---

## Distribution

1. **Canonical location.** A single stable URL the author controls — a
   personal tech blog, Substack, or equivalent. Not a Twitter thread,
   not a Notion page, not a Google Doc. The piece must be linkable two
   years from now at the same address.

2. **Format.** Long-form markdown rendered to HTML. No interactive
   elements, no JavaScript dependencies, no gated signup wall. Code
   blocks must be selectable and copyable on desktop and mobile.

3. **Channels.** The piece is written with these channels in mind for
   sharing: Hacker News, Lobste.rs, engineering-adjacent newsletters
   (Pragmatic Engineer, Bytes, TLDR-style aggregators), tech Twitter /
   Mastodon / Bluesky, internal engineering Slacks. Reader B's
   "forward to two peers" target expects these venues.

4. **Headline requirements.** The headline must do work standalone, so
   the link is shareable in DMs and on link aggregators without
   context. It must name *cognitive surrender* explicitly — the piece
   loses its reason for existing if the term isn't visible in the URL,
   title, and social card.

5. **Persistence.** No references to dated tool versions, model
   numbers, or ephemeral UI paths. *"Claude's Settings →
   Personalization"* is acceptable; *"Claude 4.7 Settings"* is not.
   The piece should still be cite-able in 2028 if Claude has changed
   UI by then.

6. **SEO posture.** Moderate. The headline should be findable by
   someone searching for *"cognitive surrender AI"* or *"Shaw Nave
   Wharton AI reasoning."* It should not be engineered for viral or
   mass-audience discovery — the target readership is specific, not
   broad.
