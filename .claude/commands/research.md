---
description: Produce a structured research brief on any topic — saved as a markdown doc with sources
allowed-tools: Read, Write, Glob, WebSearch, WebFetch, Bash(mkdir:*)
---

Two modes — first-run setup, or repeat-run research.

## Detect mode

Glob for `Resources/Config/research.md`.

- **Exists** → **Mode: Repeat Run**
- **Doesn't exist** → **Mode: First Run**

---

## Mode: First Run

### 1. Explain

"I can produce structured research briefs — deep dives saved as markdown with sources, not just a chat reply. Good for vacation destinations, before-buying research, hobbies, restaurants, anything you'd otherwise lose track of.

Set up in under a minute?"

If they decline, end.

### 2. Ask preferences

"Three quick questions:

1. **Where should briefs live?** Suggested: `References/` (already in your vault). Or somewhere else?
2. **Default depth?** Quick (~600–800 words) or thorough (1500+ words)?
3. **Default audience?** Just you, or do you sometimes share these (with family, online, etc.)?"

### 3. Save config

Create the folder if needed:

```bash
mkdir -p "References"
```

Write `Resources/Config/research.md`:

```markdown
# Research — Config

How Claude produces research briefs. Edit anytime.

## Folder

- Briefs live in: `[agreed path, default References/]`
- Filename: `[topic-slug] (Research).md` — e.g., `Tokyo Trip Planning (Research).md`

## Defaults

- **Depth:** [quick / thorough]
- **Word target:** [600–800 / 1500+]
- **Audience:** [personal / shareable]

## Document Structure

```yaml
---
categories: ["[[References]]"]
type: research
topic:
created:
sources:
---
```

Body sections (use only what's relevant — skip empty ones):

- **Summary** — 3–5 sentences. Lead with the answer.
- **Background** — context, definitions, why this matters
- **Findings** — numbered, each with inline source link
- **Data** — concrete numbers, prices, durations, ratings
- **Considerations** — risks, conflicting info, what to watch out for
- **Recommendations** — actionable next steps
- **Sources** — numbered with full citations + URLs

## Rules

- Every factual claim has a source.
- Plain language unless audience is technical.
- Lead with the most important info.
- Real numbers, not vague statements.
- If something can't be verified, say so explicitly.
- Brief should stand alone — no surrounding chat needed.
```

### 4. Show usage

"Research workflow set up. Anytime you say:
- 'Research [topic]'
- 'Deep dive into [topic]'
- 'I need to understand [topic]'
- 'Run a brief on [topic]'

…I'll produce a brief at `[path]`. Run `/research` to override defaults for a specific brief.

Want to try one now?"

If yes → continue as Repeat Run.

---

## Mode: Repeat Run

### 1. Load config

Read `Resources/Config/research.md`.

### 2. Get the topic + scope

If user already named a topic in this conversation, skip the prompt. Else:

"What topic?"

Ask **at most one** scope question if needed — e.g., "Tokyo trip — angle: food, neighborhoods, transit, or general planning?"

### 3. Research

Use WebSearch and WebFetch. Prefer authoritative sources. Capture URLs as you go.

For each finding, note the source. If sources conflict, flag it under Considerations.

### 4. Write the brief

Filename: `[Topic Title] (Research).md` in the configured folder. Title-case the topic.

Use the structure from config. Skip empty sections — don't pad. Hit the word target loosely.

Frontmatter `created:` is today's date. `sources:` is a YAML list of URLs. `topic:` is the human-readable topic.

### 5. Cross-link

If the topic relates to existing notes in the vault (e.g., a trip you have a note for, a media item), add `[[wikilinks]]` in the Background or Recommendations section.

### 6. Confirm

"Brief saved at `[path]`. [N] sources, [N] findings. Want me to dig deeper on anything?"
