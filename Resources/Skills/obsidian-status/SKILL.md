---
name: obsidian-status
description: Answer status queries and archive items in the Obsidian vault. Use when the user asks "what am I reading/watching/playing", "active projects", "pull up [title]", or says "archive [title]", "drop [title]", "mark [title] done". Handles status frontmatter mutations and read-only summaries.
---

# Vault Status & Archive

Always-on skill for asking about and updating the state of vault content. Two main jobs: answer status queries, and mutate `status:` frontmatter on existing notes.

## Triggers

- **Status queries**
  - "What am I reading?" / "Currently reading?" → media with `status: reading`
  - "What am I watching?" → `status: watching` (shows + movies in progress)
  - "What am I playing?" → `status: playing`
  - "Want to read/watch/play?" → `want-to-*` statuses
  - "What's on my list?" / "Active projects?" → `status: active` projects
  - "Pull up [title]" / "Show me [title]" → find note by fuzzy title match, summarize current state
  - "What did I [read/watch/play] this [month/year]?" → date-filtered finished items

- **Mutations**
  - "Archive [title]" → set `status: archived` (projects) or `status: dropped` (shows) or `status: read/watched/played` if completed
  - "Drop [title]" → `status: dropped`
  - "Done with [title]" / "Finished [title]" → completion status + `last:` or `finished:` to today's date
  - "I started [title]" → in-progress status (`reading`, `watching`, `playing`)
  - "Pause [title]" → `status: paused` (projects only)

## Process

### Status queries

1. Glob the relevant folder (`Media/`, `Projects/`).
2. Read frontmatter from each match. Filter by the requested status.
3. Return a concise list — one line per item, format: `Title (Type) — short context`.
   - Example: "Project Hail Mary (Book) — started 2026-04-02"
   - Example: "Severance (Show) — S2 ongoing"
4. If list is empty, say so plainly. Don't pad.

### "Pull up [title]"

1. Glob `Media/`, `Projects/` for case-insensitive title match. Use the (Type) suffix to disambiguate when multiple match.
2. If multiple matches, ask which one.
3. Read the full note. Summarize: status, key metadata, last activity date, any open thoughts/tasks.
4. End with: "What do you want to do — update status, add a note, log a thought?"

### Mutations

1. Find the note (same fuzzy-match approach as above). Disambiguate if needed.
2. Show current status and proposed change. Confirm before writing **unless** the user used a strongly imperative phrasing ("done with X", "drop X").
3. Update frontmatter:
   - `status:` to new value
   - For completion: also set `last:` (and `finished:` for books)
   - For archive on projects: also set `archived:` to today's date if that field exists in the schema
4. Don't touch the note body.
5. Confirm: "Set [Title] to `[status]`."

## Status Reference

Pull from the vault `CLAUDE.md` for canonical values. Common ones:

| Type | In progress | Done | Dropped/Archived |
|------|-------------|------|------------------|
| Book | `reading` | `read` | `dropped` |
| Movie | — | `watched` | — |
| Show | `watching` | `watched` | `dropped` |
| Game | `playing` | `played` | `dropped` |
| Project | `active`, `paused` | `completed` | `archived` |

## What NOT to do

- Don't create new notes — that's `obsidian-media` or `/research` or template-based commands.
- Don't change ratings, thoughts, or any body content.
- Don't bulk-archive without itemized confirmation.
- Don't infer "done" from context if the user didn't say so. Ask first.
- Don't touch templates, bases, or category hubs.
