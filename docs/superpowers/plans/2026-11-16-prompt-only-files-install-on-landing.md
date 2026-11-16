# Prompt-Only Files, Install on the Landing Page — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Bring `prompts/` into line with the revised reference-layer requirements: every prompt file holds its prompt and nothing else, and `prompts/README.md` carries the installation instructions for all four routes.

**Architecture:** Markdown only; nothing to build. The five prompt files are stripped to bare prompt text (no title, use-case line, Install line, code fence, or "See also"). Everything stripped that the reader still needs — install routes, use-case descriptions — moves to the landing page, which becomes its single home. `CLAUDE.md` is updated so its description of the layout stays true.

**Tech Stack:** Markdown, git, POSIX shell (`grep`, `diff`, `awk`, `wc`) for checks.

**Spec:** [REQUIREMENTS.md](../../../REQUIREMENTS.md) — working-tree version (uncommitted edits to "Structural rules" 4 and "Reference layer"). Task 1 commits it.

**Branch:** stay on `revise-defensive-prompts` (already pushed; PR not yet opened).

## Global Constraints

Copied from REQUIREMENTS.md. Every task is bound by them.

- "Every prompt file in `prompts/` contains its prompt and nothing else. Installation instructions appear in none of them; they live only on the landing page."
- "Each file must work when pasted whole or included directly in any of four places: a chat, a Claude Project, Claude's general system prompt (Settings → Personalization), or a `CLAUDE.md`."
- "`prompts/README.md` opens with the installation instructions, covering every route named under *Prompt files*. After them it lists each prompt with a link and a short description of its use."
- Selection aid on the landing page, verbatim: "If you write code daily, install the coding prompt first. If your AI use is mostly outside code, start with the general prompt."
- The landing page "shows the selection aid, the installation instructions, and a link to every prompt without scrolling, and each prompt file shows its prompt without scrolling" at 1440×900.
- Persistence: "No references to dated tool versions, model numbers, or ephemeral UI paths. *Claude's Settings → Personalization* is acceptable."
- Tone: no marketing verbs, no opening qualifiers, no reader flattery, active voice.
- Prompt wording does not change except where this plan names the line. This is a restructure, not a prompt revision.

## Review Focus

Conditions the spec implies that a reader will hit. Each has a check in the task named.

1. **A prompt line that starts with markdown syntax** (`#`, `>`, `-`, `*`, `1.`). With the fence gone, GitHub renders it as a heading or list and a copy from the rendered page differs from the file. Expected: no such line. → Task 1, Step 5.
2. **A prompt pasted somewhere that is not a Project.** A prompt that says "this project", "Settings", or "this chat" reads wrong on the other three routes. Expected: no surface words in any prompt. → Task 1, Step 5.
3. **A specialized prompt installed alone** (one chat, coding.md only). Expected: no prompt refers to the general prompt or to "the above". → Task 1, Step 5.
4. **A prompt file missing from the landing page**, or linked twice. Expected: each of the five files linked exactly once. → Task 2, Step 3.
5. **The stale UI label** *"What preferences should Claude consider in responses?"* surviving anywhere published. It is an ephemeral UI path under the Persistence rule. Expected: gone from `prompts/` and `README.md`. → Task 2, Step 3.

---

### Task 1: Strip the prompt files to prompt text

**Files:**
- Commit as-is: `REQUIREMENTS.md`
- Modify: `prompts/general.md`, `prompts/coding.md`, `prompts/decisions.md`, `prompts/research.md`, `prompts/writing.md`

**Interfaces:**
- Produces: five files whose entire content is the prompt text, ending in one newline. Task 2 links to them by filename.

- [ ] **Step 1: Commit the spec this plan implements**

```bash
git add REQUIREMENTS.md docs/superpowers/plans/2026-11-16-prompt-only-files-install-on-landing.md
git commit -m "Require prompt-only files and install instructions on the landing page"
```

- [ ] **Step 2: Run the check and watch it fail**

`22289d8` is the commit that holds the fenced versions. The check extracts each fenced block and compares it to the working file.

```bash
for f in general coding decisions research writing; do
  diff <(git show 22289d8:prompts/$f.md | awk '/^```/{f=!f;next} f') prompts/$f.md >/dev/null \
    && echo "$f ok" || echo "$f DIFFERS"
done
```

Expected now: five `DIFFERS`.

- [ ] **Step 3: In each of the five files, delete everything outside the code fence, and the two fence lines**

Removed from each: the `# Title` line, the use-case sentence, the `**Install:**` line, both ` ``` ` lines, the `---` rule, the `See also:` line, and the blank lines between them. The file's first line is the prompt's first line; its last line is the prompt's last line.

- [ ] **Step 4: In `prompts/writing.md`, make the one surface-neutral wording change**

Replace

```
Preserve my voice. If you've seen samples of my writing in this project,
point out when my draft drifts from it. Don't smooth out idiosyncrasies
that are mine on purpose.
```

with

```
Preserve my voice. If you've seen samples of my writing, point out when
my draft drifts from it. Don't smooth out idiosyncrasies that are mine
on purpose.
```

- [ ] **Step 5: Run the checks**

Rerun the Step 2 loop. Expected: `general ok`, `coding ok`, `decisions ok`, `research ok`, `writing DIFFERS` (Step 4's paragraph only — confirm with the same `diff` without `>/dev/null`).

```bash
cd prompts
P="general.md coding.md decisions.md research.md writing.md"
grep -nE '^(#|>|[-*] |[0-9]+\. |```|---)' $P                       # Review Focus 1
grep -niE 'project|settings|this chat|claude\.md' $P               # Review Focus 2
grep -niE 'general prompt|see also|install|the above' $P           # Review Focus 3
wc -l $P
```

Expected: the three `grep` commands print nothing. `wc -l` shows every file at 21 lines or fewer (the viewport proxy: about 27 lines of rendered text fit under GitHub's header at 1440×900).

- [ ] **Step 6: Commit**

```bash
git add prompts/general.md prompts/coding.md prompts/decisions.md prompts/research.md prompts/writing.md
git commit -m "Strip prompt files to prompt text only"
```

---

### Task 2: Put installation and use cases on the landing page

**Files:**
- Modify: `prompts/README.md` (whole file)

**Interfaces:**
- Consumes: the five filenames from Task 1.

- [ ] **Step 1: Run the check and watch it fail**

```bash
grep -c 'Personalization' prompts/README.md
```

Expected now: `0`.

- [ ] **Step 2: Replace `prompts/README.md` with this exact copy**

TODO(human): the four install bullets and the sentence above them are a draft. They are published text in the author's voice — rewrite them or accept them before this step runs. Constraints: all four routes named; "Settings → Personalization" spelled that way; no other UI field labels; the block stays at six lines or fewer so the page fits one screen.

```markdown
# Defensive Prompts

Each file below is a prompt and nothing else. Copy the whole file into any of these:

- **Every conversation** — Claude's Settings → Personalization.
- **One Project** — the Project's instructions.
- **One chat** — paste it as your first message.
- **Claude Code** — paste it into a `CLAUDE.md`, or include the file from one.

If you write code daily, install the coding prompt first. If your AI use is mostly outside code, start with the general prompt. Specialized prompts stack on top of the general prompt — they do not replace it.

## General prompt

- **[General](general.md)** — baseline against cognitive surrender, countering sycophancy and confidence inflation in every conversation.

## Specialized prompts

- **[Coding](coding.md)** — for building or maintaining software.
- **[Decisions](decisions.md)** — for working through a real decision — a hire, a strategy, a purchase, a plan.
- **[Research](research.md)** — for understanding something, not just getting an answer.
- **[Writing](writing.md)** — for drafting essays, posts, fiction, or anything you want to sound like you.
```

- [ ] **Step 3: Run the checks**

```bash
for f in general coding decisions research writing; do
  echo "$f $(grep -o "]($f.md)" prompts/README.md | wc -l)"       # Review Focus 4
done
grep -c 'If you write code daily, install the coding prompt first. If your AI use is mostly outside code, start with the general prompt.' prompts/README.md
grep -cE 'Personalization|Project|chat|CLAUDE\.md' prompts/README.md
grep -rn 'What preferences should Claude consider' prompts README.md  # Review Focus 5
grep -niE 'empower|unlock|transform|elevate' prompts/README.md
wc -l prompts/README.md
```

Expected: each filename counts `1`; the selection-aid count is `1`; the routes count is `4` or more; the last two `grep` commands print nothing; `wc -l` is 25 or fewer.

- [ ] **Step 4: Commit**

```bash
git add prompts/README.md
git commit -m "Move installation instructions and use cases to the prompts landing page"
```

---

### Task 3: Make CLAUDE.md describe the new layout

**Files:**
- Modify: `CLAUDE.md` — three sentences, in "Two layers", "What changes together", and "Prompt composability"

`README.md` needs no edit: its §4 links to `prompts/` and its §5 ledger entry for the selection aid ("my placement choice" on the landing page) is still true. Step 3 confirms.

- [ ] **Step 1: In "Two layers", replace the landing-page clause**

Old: `is the landing page: the selection aid and a link to each prompt.`
New: `is the landing page: the installation instructions, the selection aid, and a link to each prompt with its use case.`

- [ ] **Step 2: In "What changes together", replace the use-case bullet**

Old: `- Each prompt's use-case sentence appears twice: at the top of its own file and in the list in `prompts/README.md`.`
New: `- Installation instructions and each prompt's use-case description live only in `prompts/README.md`. A new prompt file needs a line there.`

- [ ] **Step 3: In "Prompt composability", replace the last sentence**

Old: `Every prompt file has the same shape: title, one-sentence use case, **Install** line, one code block, "See also" links to its sibling prompts.`
New: `Every prompt file holds its prompt and nothing else — no title, no install line, no code fence, no links — so it can be pasted whole into a chat, a Project, Settings → Personalization, or a `CLAUDE.md`. A prompt names no surface.`

- [ ] **Step 4: Run the checks**

```bash
grep -nE 'appears twice|Install\*\* line|one code block' CLAUDE.md
grep -n 'prompts/' README.md
```

Expected: the first prints nothing. The second prints the §4 link `(prompts/)` and the §5 link `(prompts/)`, neither pointing into a prompt file or at an anchor.

- [ ] **Step 5: Commit**

```bash
git add CLAUDE.md
git commit -m "Update CLAUDE.md for prompt-only files"
```

- [ ] **Step 6: After pushing, look at the rendered pages once**

Open `prompts/README.md` and `prompts/general.md` on GitHub in a 1440×900 window. Pass: the landing page shows install bullets, selection aid, and all five links without scrolling; the prompt shows whole without scrolling. The line counts in Tasks 1 and 2 are a proxy for this, not a replacement.
