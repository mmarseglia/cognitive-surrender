# Cognitive Surrender Publication — Drafting Plan

> **For the drafter (you or a future session):** This is a prose plan, not code. Substitutions from the generic writing-plans skill: "tests" → REQUIREMENTS.md clause checks, "commits" → USER review checkpoints (the repo is not git-initialized; see Task 0 if you want to change that), "implementation" → drafting steps with an explicit author split. Steps use `- [ ]` for tracking.

**Goal:** Produce a GitHub-hosted publication whose canonical URL is the repo's rendered `README.md`, satisfying every clause of [REQUIREMENTS.md](../../../REQUIREMENTS.md), serving both Reader A and Reader B, and linkable two years from now at the same address.

**Architecture:** Two-layer publication split across files:
- `README.md` at repo root = persuasion layer (§§1–4, ~850 words) + single-paragraph handoff block linking to the reference layer + §7 attribution at the end.
- `prompts/README.md` = reference-layer landing page. Contains §5 (general prompt with install instructions, at the top so Reader B sees a copy-pasteable block immediately) and §6 (selection aid + links to the four specialized prompt files).
- `prompts/writing.md`, `prompts/coding.md`, `prompts/research.md`, `prompts/decisions.md` = one file per specialized prompt, each independently shareable by URL.

Source material is assembled from [01-podcast-summary-cognitive-surrender.md](../../../01-podcast-summary-cognitive-surrender.md), [02-prompt-design-principles.md](../../../02-prompt-design-principles.md), [03-ready-to-use-prompts.md](../../../03-ready-to-use-prompts.md), which stay in the repo as visible working-paper-style backing material.

**Authorship split (the rule behind this plan):**
- **USER drafts** anything that carries first-person voice, author commentary, original examples, recommendations, or shareable surfaces (headline, selection aid, §1 engineering-surrender image, §3 commentary paragraph).
- **CLAUDE drafts** factual reportage (§2 study summary), mechanical assembly (§5/§6 code blocks from file 03), structural scaffolding (§4 handoff), and first passes at §7 attribution which USER then verifies.
- **Socratic gate:** Each drafting task begins with a questions step the drafter must answer *in writing* before any prose is produced. No section proceeds on implicit assumptions.

**Tech stack:** Markdown. No build, no tests, no dependencies. All verification is by spec-clause checklist.

**Word budgets (from REQUIREMENTS §Structural rules):**

- §1 Opening: 200 words hard cap, spec-driven.
- §2 Study: ~225 words.
- §3 Why this happens: ~350 words (load-bearing, largest).
- §4 Handoff: ~75 words (single signposted paragraph with links to prompts/).
- §§1–4 total: ~850 words (within the 800–1000 window).
- §7 Attribution: ~200 words.
- `README.md` total: ~1200 words (§§1–4 + handoff + §7).
- §5 General prompt (in `prompts/README.md`): ~75 words of frame + code block, block at the top so Reader B sees it without scrolling.
- §6 Selection aid (in `prompts/README.md`, below §5): ~75 words of author-voice recommendation + four file links.
- Each specialized prompt file: ~50 words of frame + install instruction + code block.

---

## Task 0: Setup and scope lock

**Files:**
- Create: `README.md` (empty, at repo root)
- Reference only: `REQUIREMENTS.md`, `01-podcast-summary-cognitive-surrender.md`, `02-prompt-design-principles.md`, `03-ready-to-use-prompts.md`

- [ ] **Step 1: Socratic checkpoint — confirm scope and naming**

**Decisions locked in (answered by USER on 2026-04-22):**
1. Publication target: GitHub repo at `cognitive-surrender/`. Canonical URL = rendered `README.md` at repo root.
2. Git: initialized. `.gitignore` excludes `.claude/`.
3. Scope vs. REQUIREMENTS.md: no changes.
4. Structure: §§1–4 + §7 in `README.md`; §5 + §6 in `prompts/README.md`; four specialized prompts split into individual files under `prompts/`.
5. CLAUDE.md visibility: kept in the repo (published) for editorial transparency.

- [ ] **Step 1: Create the empty file placeholders**

Create `README.md` at repo root with a single H1 placeholder line:

```markdown
# [headline — Task 1]
```

The `prompts/` directory and its files are created in Tasks 6 and 7, not now.

- [ ] **Step 2: Initial commit**

```bash
git add .gitignore CLAUDE.md REQUIREMENTS.md 01-podcast-summary-cognitive-surrender.md 02-prompt-design-principles.md 03-ready-to-use-prompts.md docs/ README.md
git commit -m "chore: snapshot pre-draft materials and drafting plan"
```

- [ ] **Step 3: Review checkpoint**

USER confirms the repo is initialized, README.md exists with the placeholder, and the plan is committed. Proceed to Task 1 on explicit go-ahead.

---

## Task 1: Headline, H1, and GitHub repo description

**Files:**
- Modify: `README.md` (replace H1 placeholder with the real headline).
- Apply to GitHub repo settings (not a file): repo description + topics.

**Spec clauses covered:** Distribution §4 (headline must include "cognitive surrender" explicitly, work standalone in DMs/aggregators), §6 (SEO posture — findable for *"cognitive surrender AI"* and *"Shaw Nave Wharton AI reasoning"*).

**GitHub-specific note:** A GitHub-hosted README.md does not use YAML front-matter. The "social subhead" for link previews is the repo's **Description** field, set via `gh repo edit --description "..."` or in the repo Settings UI. The **Topics** field is also set via settings and drives GitHub search (Distribution §6). Both are captured now so they're ready at push time in Task 12.

**Authorship:** USER drafts. CLAUDE offers 3–4 candidates on request; USER picks or writes fresh.

- [ ] **Step 1: Socratic checkpoint**

USER answers:
1. What verb tense and posture does the headline take? (Options: diagnostic — *"What happens when engineers stop reading AI output"*; naming — *"Cognitive surrender: the Wharton paper every AI coder should read"*; first-person — *"I stopped arguing with Copilot. Here's what Shaw & Nave say about that."* Each has tradeoffs: diagnostic is click-shareable but generic; naming is precise but dry; first-person is distinctive but narrows Reader B forwarding.)
2. Repo name (becomes part of the canonical URL): `cognitive-surrender`, or a longer variant like `cognitive-surrender-prompts`? Default: `cognitive-surrender` — the term must be visible in URL and title.
3. Repo description (≤350 chars, shown on GitHub repo page and in social cards). Must name Shaw & Nave or Wharton to do work standalone.
4. Repo topics (3–5 short tags for GitHub search). Candidates: `cognitive-surrender`, `ai`, `claude`, `prompts`, `llm-cognition`, `ai-safety`. Pick what you want.

- [ ] **Step 2: USER writes the headline into `README.md`**

Replace the placeholder:

```markdown
# [headline]
```

- [ ] **Step 3: Record the repo description and topics for Task 12 push**

Append the following to `docs/distribution-notes.md` (create if needed):

```markdown
## GitHub repo metadata

- Repo name: [chosen in step 1]
- Description: [chosen in step 1, ≤350 chars]
- Topics: [chosen list]
```

These are applied at push time in Task 12 Step 2, not committed to the README itself.

- [ ] **Step 4: Verify against Distribution §§4, 6 and Persistence (§5)**

Checklist — each must be YES:
- Headline contains the phrase "cognitive surrender."
- Headline is intelligible without context (test: imagine it pasted alone in a DM).
- No dated references in headline or description (no model versions, no "in 2026").
- Description names at least one of: Shaw, Nave, Wharton, or the study mechanism.
- Topics include `cognitive-surrender` (primary search term).

- [ ] **Step 5: Review checkpoint**

USER confirms. Move to Task 2.

---

## Task 2: §1 Opening (≤200 words, hardest section)

**Files:**
- Modify: `README.md` (append `## 1. [section title]` and body).

**Spec clauses covered:** §1 full text; Tone rules 1, 3 (no flattery, no AI-pattern prose), 4 (register); Attribution rule 1 (named sources on first use: Shaw, Nave, Wharton), rule 4 (cognitive surrender is Shaw & Nave's); Structural rule — this is where Reader A decides whether to keep reading.

**Authorship split:**
- **USER drafts** the engineering-surrender image (sentences 1–3, ~50–75 words). It must be a specific moment the user actually recognizes. An invented one will read fake and Reader A will bounce.
- **CLAUDE drafts** the pivot to Shaw & Nave (sentences 4–end, ~125 words). Factual reportage: researchers, institution, CRT study, ~50% control, confidence-rise figure. USER edits for voice.

- [ ] **Step 1: Socratic checkpoint — the image**

USER answers, in writing (not in the draft, in a scratchpad or in this conversation):
1. Which of these have you actually done in the last 30 days, and which can you describe with one specific detail?
   - Accepted a Copilot autocomplete of a function whose signature you didn't verify existed.
   - Merged an AI-suggested refactor without stepping through the diff.
   - Nodded through an AI-generated PR review.
   - Shipped code from a Cursor "apply" without reading past the first block.
   - Other: ______.
2. Pick one. What was the specific context — language, what the function was supposed to do, what the actual consequence was (caught in CI, caught in review, caught in prod, or never caught)?
3. Do you want the dark-patterns reference (social-media UI designed around cognitive vulnerabilities — REQUIREMENTS non-goal 3) here in §1 or held back for §3? Pick one; it appears exactly once in the publication.

- [ ] **Step 2: USER drafts the image**

Write ~50–75 words that open the publication. Constraints:
- Starts with the specific action, not a meta-frame. Not *"Every engineer has…"*; yes *"I accepted the autocomplete…"* or *"Last Tuesday I…"*.
- No forbidden phrases (see Tone rule 3 in REQUIREMENTS — scan for *"it's worth noting,"* *"unlock,"* *"empower,"* *"fascinating,"* triadic lists with forced parallelism).
- Does the work of distinguishing *cognitive offloading* (linter, formatter) from *cognitive surrender* (adopting output as your own thinking) — spec §1 is explicit this distinction must land.

Append to `README.md` under an H2:

```markdown
## 1. [section title, user-chosen — e.g., "The autocomplete you didn't read"]

[USER-drafted image, 50–75 words.]
```

- [ ] **Step 3: CLAUDE drafts the Shaw & Nave pivot**

CLAUDE writes ~125 words. Required content, per REQUIREMENTS §1:
- Name Shaw, Nave, Wharton on first use.
- State the headline result: participants adopted AI answers even when those answers were wrong; confidence rose ~10% regardless of correctness.
- Name *cognitive surrender* as the term and attribute it to Shaw & Nave (Attribution rule 4).
- Distinguish it explicitly from *cognitive offloading*.
- Cite the SSRN working paper by URL: https://ssrn.com/abstract=6097646.

Append below the USER image. USER then edits for voice — especially removing any residual AI-pattern prose.

- [ ] **Step 4: Verify §1 against REQUIREMENTS.md §1 checklist**

Each line must be YES:
- Total §1 ≤ 200 words (count with `wc -w` on the section).
- Engineering-surrender image in the first 3 sentences.
- Shaw, Nave, Wharton named.
- Headline finding stated (wrong-adoption + ~10% confidence rise).
- *Cognitive surrender* distinguished from *cognitive offloading*.
- Does NOT open with generic AI-doomer rhetoric, unsourced anecdote, or a personal hook that delays the finding (REQUIREMENTS §1 explicit non-pattern list).
- No forbidden phrases from Tone rule 3.

- [ ] **Step 5: Review checkpoint**

USER reads §1 aloud. If it doesn't sound like USER, revise before continuing. Move to Task 3 only on explicit go-ahead.

---

## Task 3: §2 The study (~225 words)

**Files:**
- Modify: `README.md` (append `## 2. [section title]` and body).

**Spec clauses covered:** §2 full text (CRT experiment, manipulated ChatGPT answers, ~50% control accuracy, performance falling *below* baseline when AI was wrong); Attribution rule 1 (SSRN citation); Tone rule 2 (calibrated claims — numbers carry source inline).

**Authorship:** CLAUDE drafts (factual reportage); USER verifies numbers against [01-podcast-summary-cognitive-surrender.md](../../../01-podcast-summary-cognitive-surrender.md) and the SSRN paper if they've read it.

- [ ] **Step 1: Socratic checkpoint — scope of "detail enough to be cite-able"**

USER answers:
1. Do you want the study summary to include the tri-system extension in §2, or defer tri-system to §3 where the *why* lives? (Spec allows either; the tri-system is Shaw & Nave's, so §2 is natural, but §3 currently anchors the reframe.)
2. Any number in [01-podcast-summary-cognitive-surrender.md](../../../01-podcast-summary-cognitive-surrender.md) you know is imprecise or sourced from podcast-speech rather than the paper? Flag it now so CLAUDE doesn't launder imprecision into the draft.

- [ ] **Step 2: CLAUDE drafts §2**

~225 words. Required content:
- The Cognitive Reflection Test paradigm (1 sentence — what the CRT is).
- Experimental manipulation (ChatGPT answers were manipulated — some correct, some incorrect).
- Control-group baseline (~50% accuracy).
- Treatment effect: participants followed the AI even when wrong; accuracy fell *below* baseline when the AI was wrong.
- Confidence effect (~10% rise regardless of correctness).
- SSRN citation inline.

Write in calibrated prose — every number names its source (*"Shaw & Nave report…"* not *"research shows…"*).

Append to `README.md`:

```markdown
## 2. [section title — e.g., "What Shaw and Nave actually ran"]

[CLAUDE draft, ~225 words.]
```

- [ ] **Step 3: USER verifies numbers against source material**

Read [01-podcast-summary-cognitive-surrender.md](../../../01-podcast-summary-cognitive-surrender.md) §§ describing the CRT experiment. For every number in the CLAUDE draft, mark YES if it matches the source or FIX if it doesn't. Edit inline.

- [ ] **Step 4: Verify §2 against REQUIREMENTS.md §2 checklist**

- §2 is short — this is evidence, not a lit review. Is it under ~250 words?
- Every number has a named source inline.
- No adjacent studies being catalogued (non-goal 1).
- No forbidden phrases.

- [ ] **Step 5: Review checkpoint**

USER confirms. Move to Task 4.

---

## Task 4: §3 Why this happens (~350 words, load-bearing)

**Files:**
- Modify: `README.md` (append `## 3. [section title]` and body).

**Spec clauses covered:** §3 full text (supernormal-releaser / agentic pareidolia reframe; McRaney attribution); Attribution rule 3 (McRaney's framings named with attribution on first use); Attribution rule 2 (author voice separation — first person markers); Tone rule 2 (calibrated claims).

**This section is load-bearing.** REQUIREMENTS §3 says verbatim: *"A draft that skips the reframe fails review even if every other section is strong."* Treat failure of this section as failure of the publication.

**Authorship split:**
- **CLAUDE drafts** the factual reframe (~225 words): supernormal releasers (beaver/gull examples from file 01), agentic pareidolia, the tri-system extension, attribution to McRaney where it belongs. Reportage voice.
- **USER drafts** a first-person commentary paragraph (~100 words) that connects the reframe to USER's own engineering practice. This is where the seam between reportage and author voice sits (Attribution rule 2). First-person markers required: *"my reading,"* *"I think,"* *"what this means for me,"* or equivalent. Without this paragraph, the reframe reads as received wisdom — which is exactly the behavior the piece argues against.
- **USER decides** whether the dark-patterns reference (if not placed in §1) goes here. One or two sentences max. Non-goal 3 is strict: *"Do not expand."*

- [ ] **Step 1: Socratic checkpoint — the reframe and the seam**

USER answers, in writing:
1. Of the supernormal-releaser examples in [01-podcast-summary-cognitive-surrender.md](../../../01-podcast-summary-cognitive-surrender.md) (the beaver reacting to the wrong stimulus, the gull chick pecking the exaggerated bill), which will you retain in the draft, and why? At least one concrete example should survive into §3 — abstractions about "evolved machinery" don't land on Reader A.
2. What is your *own* read on why the reframe matters for engineering work specifically? Two or three sentences, first-person. Example shape: *"My reading: Copilot isn't a neutral tool I happen to use poorly — it's a surface that recruits the same agent-detection machinery that made me mistake a shadow for a person last week. That's the piece I hadn't been able to name before this paper."* Do not copy the example; write your own.
3. Dark-patterns reference: in §1, here, or nowhere? (Default nowhere if undecided — non-goal 3 prefers restraint.)

- [ ] **Step 2: CLAUDE drafts the reframe (~225 words)**

Required content:
- McRaney named on first use with institution (*You Are Not So Smart* podcast) and attribution as the source of the reframe (distinct from Shaw & Nave's study findings).
- *Agentic pareidolia* named and attributed to McRaney.
- *Supernormal releasers* explained with at least one concrete ethology example retained from file 01 (beaver or gull).
- The tri-system extension (Shaw & Nave extending Kahneman's dual-process model) — attributed correctly.
- Explicit claim that AI prose acts on evolved machinery, not on rational evaluation — the payload of the section.

Append to `README.md`:

```markdown
## 3. [section title — e.g., "Why you can't willpower past it"]

[CLAUDE reframe draft, ~225 words.]

[USER commentary paragraph, ~100 words, first-person.]
```

- [ ] **Step 3: USER drafts commentary paragraph (~100 words, first-person)**

Answer from Socratic step 1, question 2, refined into publication voice. First-person markers visible in at least two sentences. Paragraph must connect the reframe to engineering practice specifically (not generic "AI users").

- [ ] **Step 4: Verify §3 against REQUIREMENTS.md §3 checklist and Attribution rules 2, 3**

- McRaney attributed correctly (for *agentic pareidolia*, *supernormal releasers*, not for the study itself).
- Shaw & Nave attributed correctly (for *cognitive surrender*, CRT, tri-system — Attribution rule 4).
- At least one concrete ethology example survived.
- First-person seam is visible (Attribution rule 2).
- Dark-patterns reference, if present, is ≤ 2 sentences and does not expand (non-goal 3).
- §3 reads as *the* load-bearing section — if you deleted it, would the argument collapse? (Yes = pass.)
- No forbidden phrases.

- [ ] **Step 5: Review checkpoint**

USER reads §§1–3 together aloud and listens for a voice break at the §3 USER paragraph. If the seam is invisible, revise to make it visible — the anti-surrender claim depends on readers being able to tell which voice is which.

---

## Task 5: §4 Handoff (~75 words)

**Files:**
- Modify: `README.md` (append `## 4. [section title]` and body).

**Spec clauses covered:** §4 full text (clearly-marked paragraph signposting the shift to reference layer); Structural rule 3 (transition rule — a single, explicit, signposted handoff); independence rule 2 (Reader B uses this to skip ahead, Reader A uses it to pace the shift).

**Authorship:** CLAUDE drafts (structural scaffolding); USER edits for voice.

**Structure note:** The handoff is the bridge between `README.md` and the linked reference-layer files. It must contain a direct link to `prompts/README.md` (which holds §5 + §6) so Reader B reaches the first copy-pasteable prompt with exactly one click and no subsequent scroll.

- [ ] **Step 1: Socratic checkpoint**

USER answers:
1. Visual signpost treatment: blockquote (`> If you want tools…`), pull-out H2, bold lead-in line, or italicized paragraph? Pick one. REQUIREMENTS §4 requires it be clearly marked but doesn't specify the mechanism.
2. Link target phrasing: one link (*"→ [the prompts](prompts/)"*), two links (*"→ [general prompt](prompts/) and [specialized prompts](prompts/#specialized)"*), or something else? One is cleaner; two makes Reader B's first-click target explicit.
3. Word for what the reference layer gives them: *"prompts,"* *"installable defenses,"* *"tools,"* *"counter-surface"*? Pick one and use it consistently in §4, `prompts/README.md`, and the specialized prompt files.

- [ ] **Step 2: CLAUDE drafts the handoff**

~75 words, one paragraph. Required:
- Names the shift from *why* to *how*.
- Tells Reader B they can skip to the prompts (target action: install) — with the link(s) USER chose in step 1.
- Tells Reader A the next part is where the argument becomes operational.
- Signpost chosen in step 1.
- Ends the persuasion-layer reading experience: the next thing visible is §7 attribution (not a prompt block), so the handoff has to be unambiguous that the prompts live one click away, not further down the page.

Append to `README.md`:

```markdown
## 4. [section title — e.g., "If you want tools rather than argument"]

[CLAUDE draft, ~75 words, with USER-chosen signpost and link to prompts/.]
```

- [ ] **Step 3: Verify against REQUIREMENTS.md §4 and Structural rules 2, 3**

- Handoff is a single paragraph (not interleaved with earlier argument).
- Both reader paths addressed.
- Link to `prompts/README.md` is visible and clickable.
- Signpost is visible on scroll.
- No interleaving — no prompt text leaks into `README.md` before the attribution.

- [ ] **Step 4: Time-to-value check for §§1–4**

Run word count on §§1–4 combined:

```bash
awk '/^## 1\./,/^## 7\./' README.md | sed '/^## 7\./d' | wc -w
```

Expected: 800–1000 words (the §§1–4 persuasion layer, before §7 attribution). If over, trim §3 first (largest budget), then §2. If under, expand §3 commentary (the author's seam paragraph tolerates growth more than the reportage does).

- [ ] **Step 5: Review checkpoint**

USER confirms persuasion layer is complete and within word budget. Move to Task 6.

---

## Task 6: §5 The general prompt (`prompts/README.md`, first half)

**Files:**
- Create: `prompts/README.md` with §5 at the top.

**Spec clauses covered:** §5 full text (general prompt from file 03 as a single copy-pasteable code block; Claude install instructions — Settings → Personalization); Structural rule 4 (Reader B must reach the first copy-pasteable prompt within one scroll-screen of arriving at the reference layer); out of scope: install paths for ChatGPT, Gemini.

**Structure note:** `prompts/README.md` is the reference-layer landing page. GitHub renders it automatically when a reader navigates to `prompts/`. This task populates only the top half of that file (§5 general prompt). Task 7 adds the §6 selection aid below §5 and creates the four specialized prompt files that this page links to.

**Authorship:** CLAUDE assembles from [03-ready-to-use-prompts.md](../../../03-ready-to-use-prompts.md). USER verifies the prompt text matches file 03 exactly (or decides deliberately what to diverge on).

- [ ] **Step 1: Socratic checkpoint**

USER answers:
1. Paste the prompt as it exists in file 03, or revise for the publication? (Default: paste verbatim. Revision triggers a parallel edit to file 03 to keep them in sync, or a note in §7 acknowledging the publication-version divergence.)
2. Frame paragraph tone: one-sentence (*"Paste this into Claude's Settings → Personalization."*) or short rationale paragraph? One-sentence is strongly preferred so the code block sits near the top of the viewport. The selection aid lives below, not above, the general prompt.
3. Page title at the top of `prompts/README.md` — e.g., *"Prompts"*, *"Installable prompts"*, *"Cognitive-surrender counter-prompts"*? Pick one; it's the first thing Reader B sees after clicking through.

- [ ] **Step 2: CLAUDE creates `prompts/README.md` with §5 at the top**

Required content, in order:
- H1 page title chosen in step 1.
- One-sentence frame (or very short paragraph).
- Install path: *"Paste into Claude → Settings → Personalization."* No dated model references (Distribution §5).
- General prompt as a fenced code block, plain fence (no language tag).

Create `prompts/README.md`:

````markdown
# [Page title]

[One-sentence frame.]

**Install:** Claude → Settings → Personalization → paste into the custom instructions field.

```
[Full text of the general prompt from file 03.]
```
````

Leave the rest of the file empty for now (Task 7 appends the selection aid and links).

- [ ] **Step 3: USER verifies the prompt text against [03-ready-to-use-prompts.md](../../../03-ready-to-use-prompts.md)**

Diff visually. If divergence is accidental, fix. If deliberate, add a note in §7 attribution later.

- [ ] **Step 4: Verify §5 against REQUIREMENTS.md §5 checklist and Structural rule 4**

- Single copy-pasteable block (not broken across multiple blocks).
- Install path named.
- No non-Claude install paths (ChatGPT, Gemini, etc. — out of scope).
- First prompt visible at the top of `prompts/README.md` on a 1440×900 viewport. If the page title + frame + install line push the code block below the fold, shorten.
- File location is `prompts/README.md` (not `prompts/general.md`) so GitHub renders it as the folder's landing page.

- [ ] **Step 5: Review checkpoint**

USER confirms. Move to Task 7.

---

## Task 7: §6 Selection aid + four specialized prompt files

**Files:**
- Modify: `prompts/README.md` (append §6 selection aid and links section below the general prompt).
- Create: `prompts/writing.md`
- Create: `prompts/coding.md`
- Create: `prompts/research.md`
- Create: `prompts/decisions.md`

**Spec clauses covered:** §6 full text (four project prompts — writing, coding, research, decisions; each named with its use case; installed as Claude Project system prompts; selection aid verbatim or equivalent); Attribution rule 5 (the selection-aid recommendation is author commentary, marked as such).

**Structure note:** Each specialized prompt gets its own file so it has an independent canonical URL Reader B can forward. The selection aid lives on `prompts/README.md` below §5 — that's the page Reader B lands on, and the aid must appear there so they see it before picking a prompt.

**Authorship split:**
- **USER drafts** the selection aid (~75 words). It is a recommendation — it originates with the author (Attribution rule 5). CLAUDE will offer candidate phrasings, but the final choice and voice are USER's.
- **CLAUDE assembles** the four specialized prompt files from [03-ready-to-use-prompts.md](../../../03-ready-to-use-prompts.md), one file per prompt.

- [ ] **Step 1: Socratic checkpoint**

USER answers:
1. The REQUIREMENTS.md example selection aid is: *"If you write code daily, install the coding prompt first. If your AI use is mostly outside code, start with the general prompt."* Accept as-is, adapt, or rewrite?
2. Order of the four prompt links on the landing page: by use-case frequency (coding, writing, decisions, research — coding first for Reader A) or by alphabetical (coding, decisions, research, writing)? Pick one and state the reason in or just after the selection aid.
3. Individual prompt file names: `prompts/writing.md` / `prompts/coding.md` / `prompts/research.md` / `prompts/decisions.md` (short and URL-clean, default), or something more descriptive (`prompts/writing-and-editing.md`)? Default is preferred for forwardability.
4. Any of the four prompts in file 03 you now want to revise before publishing? If yes, handle in a separate task — do not let it delay §6.

- [ ] **Step 2: USER drafts selection aid (~75 words)**

First-person-adjacent is fine (Attribution rule 2). Must include:
- A recommendation on which prompt to install first for Reader A's engineering case.
- A recommendation for readers whose AI use is mostly outside code.
- A note that specialized prompts stack on top of the general prompt — not replace it. (This is a composability fact from [CLAUDE.md](../../../CLAUDE.md) "Prompt composability" section.)

- [ ] **Step 3: CLAUDE appends §6 to `prompts/README.md`**

Below the §5 general prompt block, append:

````markdown
## Specialized prompts

[USER selection aid, ~75 words.]

- **[Writing](writing.md)** — [one-line use case]
- **[Coding](coding.md)** — [one-line use case]
- **[Research](research.md)** — [one-line use case]
- **[Decisions](decisions.md)** — [one-line use case]
````

Order and one-line use cases chosen in step 1.

- [ ] **Step 4: CLAUDE creates the four specialized prompt files**

For each of `prompts/writing.md`, `prompts/coding.md`, `prompts/research.md`, `prompts/decisions.md`:

````markdown
# [Prompt name]

[One-sentence use-case frame.]

**Install:** Claude → create a new Project → paste into the project's system prompt.

```
[Full text of the specialized prompt from file 03.]
```

---

See also: [general prompt and other specialized prompts](README.md).
````

The trailing back-link to `prompts/README.md` is required so a reader who lands on one specialized prompt via a forwarded URL can reach the general prompt and the others.

- [ ] **Step 5: Verify §6 against REQUIREMENTS.md §6 checklist**

- All four specialized prompts exist as their own files, each with its own canonical URL.
- Each names its use case in the frame and in the `prompts/README.md` link list.
- Each is installed as a Claude Project system prompt (the spec is explicit — not Personalization).
- Selection aid is present on `prompts/README.md` below §5, readable as author commentary (not laundered as fact).
- Prompt texts match file 03 (or divergence is deliberate and noted in §7).
- Each specialized file has a back-link to `prompts/README.md`.

- [ ] **Step 6: Review checkpoint**

USER confirms. Move to Task 8.

---

## Task 8: §7 Closing attribution

**Files:**
- Modify: `README.md` (append `## 7. [section title]` and body).

**Spec clauses covered:** §7 full text (explicitly names which claims originated with Shaw & Nave, which with McRaney, which with the author, plus the selection aid as author contribution); Attribution rules 1–5 in full; Tone rule 2 (calibrated claims).

**This section is non-negotiable.** REQUIREMENTS §7 says verbatim: *"a publication about cognitive surrender whose attribution is blurry discredits itself."*

**Authorship split:**
- **CLAUDE drafts** the first pass — a clean three-bucket split (Shaw & Nave / McRaney / author).
- **USER verifies and revises** — only USER knows what counts as author contribution in full (examples chosen, reframes, recommendations, the selection aid, the specific engineering-surrender image in §1).

- [ ] **Step 1: Socratic checkpoint**

USER answers:
1. Any contributions in §§1–6 that are borrowed from someone other than Shaw, Nave, or McRaney that need their own bullet? (Kahneman on dual-process is a likely candidate — Shaw & Nave *extend* it with the tri-system, but dual-process itself is Kahneman's and should probably be named once.)
2. For the author contributions bullet, list every item you want acknowledged — §1 engineering-surrender image, §3 commentary paragraph, §6 selection aid, any reframes in §§1–4, the organizational choice to split persuasion from reference.

- [ ] **Step 2: CLAUDE drafts §7**

~200 words. Structure:
- One-sentence opener that states the attribution discipline.
- Three buckets:
  - **Shaw & Nave (Wharton):** *cognitive surrender* (distinct from *cognitive offloading*); the Cognitive Reflection Test experiment and its findings; the ~10% confidence-inflation result; the tri-system extension of Kahneman's dual-process model. SSRN link.
  - **David McRaney (*You Are Not So Smart*):** *agentic pareidolia* as a coinage; the application of *supernormal releasers* to LLM interfaces; the framing that AI prose acts on evolved machinery.
  - **Author:** the engineering-specific framing and examples; the §1 surrender image; the organizational split between persuasion and reference layers; the selection aid in §6; the commentary paragraph in §3.
- Optional: Kahneman named once for dual-process.
- Closing one-liner if needed (no filler recap).

Append to `README.md`:

```markdown
## 7. [section title — e.g., "Attribution"]

[CLAUDE draft, ~200 words, three-bucket.]
```

- [ ] **Step 3: USER revises**

Walk through each bullet and mark accurate / inaccurate / missing. Revise inline.

- [ ] **Step 4: Verify §7 against REQUIREMENTS.md §7 and Attribution rules 1–5**

- Every named source is attributed correctly (double-check: *agentic pareidolia* is McRaney, not Shaw & Nave; *cognitive surrender* is Shaw & Nave, not McRaney).
- Author contributions are listed and visible.
- SSRN link present.
- Attribution is not blurry — a skeptical reader could write the three-bucket split themselves after reading this section.

- [ ] **Step 5: Review checkpoint**

USER confirms. Persuasion + reference layers are now complete; move to full-document review.

---

## Task 9: Full-document spec compliance review

**Files:**
- Read: `README.md`, `prompts/README.md`, `prompts/writing.md`, `prompts/coding.md`, `prompts/research.md`, `prompts/decisions.md`, `REQUIREMENTS.md`.

**Spec clauses covered:** all of REQUIREMENTS.md — cross-file constraints that no single-section check catches.

- [ ] **Step 1: Spec-clause traceability matrix**

Open all six publication files alongside `REQUIREMENTS.md`. For every numbered clause in REQUIREMENTS (Purpose, Reader personas, Success criteria 1–4, Structural rules 1–4, §§1–7, Tone rules 1–5, Attribution rules 1–5, Non-goals, Distribution 1–6), mark PASS or FIX with a one-line note that names the file the clause lives in.

Produce the matrix as a scratch file or inline in the conversation — do not commit to the repo. Fix any FIXes inline in the relevant file, then mark PASS and move on.

Particular cross-file checks that need explicit attention:
- Two-layer rule: no prompt text appears in `README.md` (the persuasion layer), and no persuasion argument appears in `prompts/*` files (the reference layer).
- Independence rule: a reader who lands on `prompts/README.md` from a forwarded URL can use it without reading `README.md` first. Conversely, `README.md` stands alone if the reader never clicks through to `prompts/`.
- Attribution: the §7 attribution block on `README.md` is the single canonical attribution; no competing attribution blocks on `prompts/*` files.

- [ ] **Step 2: Dual-reader walk-through**

USER reads as Reader A (motivation-gap engineer who has never heard of cognitive surrender): does `README.md` hold them? Do they reach §4 without bouncing? Do they click through from the handoff to `prompts/` and plausibly install the general prompt?

USER reads as Reader B (ammunition-gap engineer who already agrees): can they reach `prompts/README.md` directly from the `README.md` handoff with one click? Once on `prompts/README.md`, is the general-prompt code block visible at the top of the first viewport? Do they have a link they would forward to two peers? Does the headline survive as a DM-able link?

If either path fails, identify the file and section and revise.

- [ ] **Step 3: Non-goals check**

Scan across all files for drift:
- Any paragraph that catalogs adjacent AI-cognition studies beyond Shaw & Nave? (Non-goal 1.) Cut.
- Any paragraph blaming the tool rather than describing what it exploits in us? (Non-goal 2.) Rewrite.
- More than one or two sentences on social-media dark patterns? (Non-goal 3.) Cut to a single gesture.
- Any AI-risk territory — existential risk, autonomous-agent risk, alignment, labor displacement? (Non-goal 4.) Cut.

- [ ] **Step 4: Review checkpoint**

USER signs off on spec compliance. Move to Task 10.

---

## Task 10: Tone pass

**Files:**
- Modify (as needed): `README.md`, `prompts/README.md`, `prompts/writing.md`, `prompts/coding.md`, `prompts/research.md`, `prompts/decisions.md` — edits throughout based on forbidden-phrase scans. The tone rules apply to every word the author wrote; they do *not* apply inside the fenced prompt code blocks (those are verbatim prompt text and shouldn't be rewritten even if a phrase looks awkward).

**Spec clauses covered:** Tone rules 1–5 in full.

- [ ] **Step 1: Forbidden-phrase grep**

Run each of these across all publication files. Each match is a FIX unless it is inside a fenced code block (inspect the hit before editing):

```bash
grep -niE "it's worth noting|it's important to|in this piece|we will explore|this is a fascinating|certainly|great question" README.md prompts/README.md prompts/writing.md prompts/coding.md prompts/research.md prompts/decisions.md
grep -niE "empower|unlock|transform|elevate|leverage(s|d)? the power of|harness(es|ed)?" README.md prompts/README.md prompts/writing.md prompts/coding.md prompts/research.md prompts/decisions.md
grep -niE "it could be argued|some might say|arguably|one could" README.md prompts/README.md prompts/writing.md prompts/coding.md prompts/research.md prompts/decisions.md
grep -niE "In conclusion|To summarize|In summary|As discussed above" README.md prompts/README.md prompts/writing.md prompts/coding.md prompts/research.md prompts/decisions.md
```

For each hit outside a code block: either delete the phrase or replace with a direct claim.

- [ ] **Step 2: Triadic-list scan**

Scan `README.md` visually for lists of three items where two would do (Tone rule 3, fourth bullet). Examples: *"clear, concise, and compelling,"* *"fast, reliable, and scalable."* If the third item isn't carrying its own weight, delete it. This check is narrowest in §§1–4 and §7 — not inside prompts.

- [ ] **Step 3: Reader-directed flattery scan**

Search for phrases that praise the reader for reading, asking questions, or engaging with hard topics (Tone rule 1). Typical forms: *"if you've read this far,"* *"for the curious reader,"* *"those willing to think deeply."* Delete.

- [ ] **Step 4: Calibrated-claim scan**

For every number, name, or study claim in `README.md`, verify it's attributed inline (Tone rule 2). For every inferential claim, verify it's marked as such (*"my reading,"* *"a reasonable inference,"* *"not stated directly in the paper, but…"*). If reportage and commentary blur anywhere, add the marker.

- [ ] **Step 5: Active-voice scan**

Find passive constructions in `README.md`. For each: is it displacing a subject correctly (*"participants' confidence rose"*), or is it hedging ownership (*"mistakes were made"*)? Fix the hedging ones.

- [ ] **Step 6: Review checkpoint**

USER reads `README.md` aloud end to end, then skims `prompts/README.md` and one specialized file. Any passage that sounds like it could be in a generic AI-risk blog post gets rewritten or cut (CLAUDE.md voice rule).

---

## Task 11: Time-to-value and layout checks

**Files:**
- Read: `README.md`, `prompts/README.md`, and one specialized prompt file.

**Spec clauses covered:** Structural rule 4 (time-to-value constraints — persuasion layer ≤ ~4 min, first copy-pasteable prompt within one scroll-screen of the reference layer start).

- [ ] **Step 1: Persuasion-layer word count**

```bash
awk '/^## 1\./,/^## 7\./' README.md | sed '/^## 7\./d' | wc -w
```

Target: 800–1000 words for §§1–4. If outside, revise §3 (has the most slack).

- [ ] **Step 2: Reference-layer first-prompt position check**

GitHub renders `prompts/README.md` automatically when a reader navigates to `/prompts/`. Open the rendered page on a 1440×900 viewport. The §5 general-prompt code block must be visible without scrolling past one screen from the top of the page.

If the page title + one-sentence frame + install line push the code block below the fold, shorten the frame to one line or reduce the H1 to H2.

- [ ] **Step 3: Code-block copyability check**

On desktop and mobile, each code block must be selectable and copyable. GitHub adds a copy button automatically; verify that the default triple-click-and-drag selection also works for readers who don't see the button. Test in the rendered GitHub view on `prompts/README.md` and on one specialized file.

- [ ] **Step 4: Link-path integrity**

From `README.md`:
- `prompts/` link resolves to `prompts/README.md` on GitHub (test by clicking in the rendered view).

From `prompts/README.md`:
- Each of the four specialized prompt links (`writing.md`, `coding.md`, `research.md`, `decisions.md`) resolves.

From each specialized file:
- The back-link to `README.md` (the one inside `prompts/`) resolves.

- [ ] **Step 5: Review checkpoint**

USER confirms time-to-value and layout. Move to Task 12.

---

## Task 12: Distribution prep

**Files:**
- Modify: `README.md`, `prompts/README.md`, specialized prompt files as needed (final adjustments to headline, lingering dated references, repo metadata).
- Optional: Create `docs/distribution-notes.md` capturing where the piece will be posted and in what order.

**Spec clauses covered:** Distribution §§1–6 in full.

- [ ] **Step 1: Persistence scan**

Search for dated references that would rot, across all publication files:

```bash
grep -niE "Claude [0-9]+\.[0-9]+|GPT-[0-9]|Cursor [0-9]|as of (today|this week|this month|202[5-9])" README.md prompts/README.md prompts/writing.md prompts/coding.md prompts/research.md prompts/decisions.md
```

Each hit is a FIX. Replace with version-free phrasing (*"Claude's Settings → Personalization"*, not *"Claude 4.7 Settings"*).

- [ ] **Step 2: Canonical URL and repo metadata**

USER confirms:
- The GitHub repo is named so the URL reads well as the canonical link — e.g., `github.com/<user>/cognitive-surrender` rather than something generic. Rename the repo before pushing if needed.
- The repo's GitHub **description** field (set in repo settings) mirrors the social subhead from Task 1.
- The repo has a **topic** or two (e.g., `ai`, `cognitive-surrender`, `claude`) for discoverability (Distribution §6 — moderate SEO).
- README.md headline matches what GitHub renders at the top of the repo page.

- [ ] **Step 3: Social card preview**

GitHub generates Open Graph previews automatically from the repo's description and `README.md` H1. USER tests by pasting the repo URL into a Slack DM to themselves after pushing — the preview card should show the headline and the subhead, with the term *cognitive surrender* visible.

- [ ] **Step 4: First-push-and-publish checklist**

Before the first `git push`:
- Branch is `main` (GitHub default).
- No uncommitted changes.
- All files except `.claude/` are tracked.
- `git log --oneline` shows a clean commit sequence (this plan assumes per-task commits — see individual task review checkpoints).

Create the GitHub repo (via `gh repo create <name> --public --source=. --push` if the `gh` CLI is available, or manually on the web and then `git remote add origin ... && git push -u origin main`).

- [ ] **Step 5: Channel list**

Optional scratch file `docs/distribution-notes.md` — not published, just USER's notes — listing the first 3–5 channels to share to (Hacker News, Lobste.rs, relevant newsletter editors, specific Slack workspaces). Reader B's "forward to two peers" target assumes these surfaces exist.

- [ ] **Step 6: Review checkpoint — ready to publish**

USER confirms the publication is ready and the repo is pushed. The plan is complete.

---

## Self-review (ran after plan was written)

**Spec coverage check.** Walked REQUIREMENTS.md section by section:

- Purpose → Task 0 scope lock + Task 9 dual-reader walk-through.
- Reader personas → Task 9 step 2 (explicit dual-reader test).
- Success criteria 1–2 (outcome) → Not testable from draft alone; documented as the target in the plan header.
- Success criteria 3 (one-sentence recall of the Shaw & Nave finding) → enforced in §1 (Task 2) and re-checked in Task 9.
- Success criteria 4 (comprehension without action = failure) → addressed by §4 handoff (Task 5) and the one-scroll-screen test (Task 11).
- Structural rules 1–4 → Task 5 (transition), Task 11 (time-to-value).
- §§1–7 content requirements → Tasks 2, 3, 4, 5, 6, 7, 8 one-to-one.
- Tone rules 1–5 → Task 10.
- Attribution rules 1–5 → distributed across Tasks 2, 3, 4, 7, 8 and verified in Task 9.
- Non-goals 1–4 → Task 9 step 3.
- Distribution §§1–6 → Task 12.

**Placeholder scan.** No "TBD," no "implement later," no "similar to Task N." Socratic questions are explicit, draft splits are explicit, verification checklists are explicit.

**Type consistency.** The same word choices (e.g., "persuasion layer" / "reference layer," "selection aid") are used across tasks. Word budgets are internally consistent: §§1–4 sum to ~850 (within 800–1000).

**One gap noted and patched inline:** The original draft of Task 6 did not specify whether the four prompts should go in a user-chosen order or a fixed order. Added Socratic question 2 to Task 6 step 1 to force the choice.

---

## Plan revision 2026-04-22 (structure change before Task 1)

USER chose GitHub as the publishing surface, which changed the architecture before any subagent was dispatched. Deltas:

- Single-file `publication.md` → multi-file publication with `README.md` at the repo root + `prompts/` directory.
- §§5 and §6 moved out of the persuasion-layer file into `prompts/README.md`.
- Specialized prompts split into four individually-URL-able files: `prompts/writing.md`, `prompts/coding.md`, `prompts/research.md`, `prompts/decisions.md`.
- Tasks 5, 6, 7, 9, 10, 11, 12 rewritten to reflect the multi-file layout; Tasks 2, 3, 4, 8 unchanged in substance (targets still land in `README.md`).
- Task 1 switched from YAML front-matter (unsupported in GitHub READMEs) to H1-only + repo description/topics captured in `docs/distribution-notes.md` and applied at push time in Task 12.
- Time-to-value test in Task 11 now checks that Reader B's path = one click from handoff to `prompts/README.md`, with the general-prompt code block at the top of the viewport.
- The handoff in Task 5 is a link to `prompts/` rather than a `---` divider inside a single file.
- Initial commit consolidated into Task 0 Step 2 (snapshot of existing materials + plan + README placeholder, single commit).
- `.gitignore` added to keep `.claude/` out of the published repo.

**Re-checked spec coverage after the rewrite:** All REQUIREMENTS.md clauses still map to tasks. The two-layer rule (Structural rule 1), independence rule (Structural rule 2), and time-to-value constraints (Structural rule 4) are strengthened by the multi-file layout — persuasion and reference layers literally cannot interleave because they're separate files.

**Re-checked placeholder scan:** No new placeholders introduced. All Socratic questions remain explicit.

