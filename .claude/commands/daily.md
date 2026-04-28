---
description: Brain dump → structured daily note. Carries forward unfinished items. First run sets up the config.
allowed-tools: Read, Write, Edit, Glob, Bash(date:*), Bash(mkdir:*)
---

Two modes — first-run setup, or repeat-run capture.

## Detect mode

Glob for `Resources/Config/daily.md`.

- **Exists** → **Mode: Repeat Run**
- **Doesn't exist** → **Mode: First Run**

---

## Mode: First Run

User hasn't configured daily notes yet. Walk through it conversationally.

### 1. Explain

"Daily notes are simple: end of day, tell me what you did. I turn the brain dump into a structured note saved to `Daily/`. Over time it becomes a searchable record — useful for recall, week reviews, or just remembering when you did that thing.

Want to set this up? Takes a minute."

If they decline, end. Run again anytime.

### 2. Propose template

"Here's the default. Most people use it as-is — say so or tell me what to tweak.

```markdown
# YYYY-MM-DD — Day of Week

## Did Today
- [What got done + brief why-it-mattered]

## Open
- [ ] [Carried forward and new — action-oriented]

## Notes
[Observations, ideas, things to remember]
```

Built-in behaviors:
- Multiple brain dumps in one day → append, don't overwrite
- Open `- [ ]` items from the most recent prior daily note carry forward (marked carried)
- Sundays add a **Week Ahead** section with top priorities

Adjust anything?"

Wait. Iterate if they want changes. Don't push.

### 3. Save the config

Write `Resources/Config/daily.md`:

```markdown
# Daily Notes — Config

How Claude creates and updates daily notes. Edit anytime.

## Folder

- Daily notes: `Daily/`
- One file per day, named `YYYY-MM-DD.md`

## Template

[Final template from step 2]

## Behaviors

- Never overwrite an existing daily note. If today's exists, read it and append.
- Carry forward unchecked `- [ ]` items from the most recent prior daily note. Mark with `(carried)`.
- Ask clarifying questions for vague items — capture what got done and why it mattered, not minute-by-minute play-by-play.
- Capture facts, not judgments. Don't label something a win unless the user said so.
- On Sundays, add **Week Ahead** with top 3 priorities for next week + stretch goals.
[Any user-requested behaviors]
```

### 4. Optionally try now

"Config saved. Want to log today now, or come back later?"

If yes → continue as if Repeat Run.

---

## Mode: Repeat Run

Setup is done. Just capture.

### 1. Load config

Read `Resources/Config/daily.md` for template + behaviors.

### 2. Get today's date

`date +%Y-%m-%d` and `date +%A`.

### 3. Check for today's note

Glob `Daily/YYYY-MM-DD.md`.

- Exists → read it. You'll append, not replace.
- Missing → you'll create it.

### 4. Carry-forward check

Glob `Daily/*.md`, sort by filename (newest first), find the most recent file *before* today. Read it, extract unchecked `- [ ]` items. Bring them into today's `## Open` marked `(carried)`.

### 5. Get the brain dump

If the user already brain-dumped in this conversation, skip the prompt. Otherwise:

"What'd you do today?"

### 6. Write the note

Apply template + behaviors from config. Turn messy input into structured content. Ask 1–2 clarifying questions for vague items before writing.

If today is Sunday, add a `## Week Ahead` section. Ask for top 3 priorities if not mentioned.

### 7. Confirm

"Logged at `Daily/YYYY-MM-DD.md`. [N] done, [N] open ([N] carried)."

Flag anything ambiguous: "Wasn't sure about [item] — more context?"
