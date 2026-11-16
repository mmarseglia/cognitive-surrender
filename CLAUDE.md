# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

A published essay plus installable Claude prompts about **cognitive surrender** — Shaw & Nave's (Wharton) term for adopting AI output without verification and treating it as your own reasoning. The publication has one job: move a software engineer from meeting the idea to installing a prompt.

The entire deliverable is markdown. There is nothing to build or test.

[REQUIREMENTS.md](REQUIREMENTS.md) is the contract. Read it before editing published text: it defines the two reader personas, the tone rules, the attribution rules, and the non-goals every edit is measured against.

## Two layers

- **Persuasion layer** — [README.md](README.md). The essay: the merge anecdote, the Cognitive Reflection Test study, McRaney's supernormal-releaser reframe, the handoff, the attribution ledger.
- **Reference layer** — [prompts/](prompts/). [prompts/README.md](prompts/README.md) is the landing page: the installation instructions, the selection aid, and a link to each prompt with its use case. `general.md` holds the general prompt; `coding.md`, `decisions.md`, `research.md`, and `writing.md` each hold one specialized prompt.

Prompt text lives in the reference layer only. The essay links there once, from its §4 handoff. Each layer must stand alone: a reader who skips the essay still gets everything from `prompts/`.

`docs/` is author-facing and unpublished: the drafting plan and distribution notes.

Two mismatches to know about:

- **Section numbers.** REQUIREMENTS.md numbers the publication §1–§7 across both layers. Its §5 is `prompts/general.md` and its §6 is the rest of `prompts/`; its §7 is README.md's §5 Attribution.
- **Missing source files.** The drafting plan in `docs/` cites `01-podcast-summary-cognitive-surrender.md`, `02-prompt-design-principles.md`, and `03-ready-to-use-prompts.md`. Those files are absent from this repo and its history. README.md and `prompts/` are the source of truth now.

## What changes together

- A claim, coinage, or framing edited in README.md §§1–4 needs its line in the §5 attribution ledger updated. The ledger says who originated what — Shaw and Nave, McRaney, Kahneman, or the author — down to individual labels.
- Installation instructions and each prompt's use-case description live only in `prompts/README.md`. A new prompt file needs a line there.
- The four mechanism names (confidence inflation, zero friction, ownership confusion, bypassed deliberation) appear in README.md §4 and are attributed one by one in §5.

## Editorial voice — non-negotiable

The essay argues that AI-shaped rhetoric acts on human cognition. AI-shaped prose inside it falsifies the thesis line by line. The full rules are REQUIREMENTS.md "Tone and voice" and "Attribution"; the ones that decide most edits:

- **Name the source.** Shaw and Nave, McRaney, Kahneman, Tinbergen — by name, at the claim.
- **Keep the seam visible.** The author's commentary is first person; the researchers' findings are reportage.
- **Calibrated numbers.** "About 10%", "roughly 50%" — carry the precision the source carries.
- **Concrete over abstract.** The herring gull chick pecking the painted stick and the MCP middleware merge carry the argument. New material follows that pattern.
- **Undated.** Name Claude surfaces without model versions or version-specific UI paths, so the piece stays citable.

If an edit would fit comfortably in a generic AI-risk blog post, it violates the voice.

## Prompt composability

The prompts are a layered system:

- The **general prompt** is tuned for everyday lookups — it corrects sycophancy and uncertainty without being obstructive.
- The **specialized prompts** go further on the axis that matters in their domain, and assume the general prompt is already loaded. The research prompt's Socratic mode is the example: right for a learning Project, annoying as a global default.

A specialized prompt carries only directives the general prompt lacks. After changing a general-prompt directive, check all four specialized prompts for contradiction.

Every prompt file holds its prompt and nothing else — no title, no install line, no code fence, no links — so it can be pasted whole into a chat, a Project, Settings → Personalization, or a `CLAUDE.md`. A prompt names no surface.
