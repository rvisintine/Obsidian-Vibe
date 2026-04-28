---
description: Vault menu — set up workflows, capture something, or figure out what to work on
allowed-tools: Read, Glob
---

Single entry point for vault operations. Show the menu, route to the right command or skill.

## Check onboarding

Read vault root `CLAUDE.md`. If no `## About Me` section exists, suggest: "Haven't run `/vault-onboard` yet — want to do that first? It teaches me who you are. Or skip and pick from the menu."

## Menu

Present:

"What do you want to do?

**Capture**
1. Log today — brain dump → daily note (`/daily`)
2. Add media — book, movie, show, game (`/media` or just say "I just finished X")
3. Quick capture — drop a note in `Inbox/` to process later

**Plan & explore**
4. Research a topic — deep dive saved as a brief (`/research`)
5. Brainstorm — guided questions to surface what's on your mind (`/brainstorm`)
6. Start a project — create a project note with structure

**Maintain**
7. Vault health check — fix links, properties, orphans (`/maintain`)
8. Update profile — re-run `/vault-onboard`

Pick a number, name, or just tell me what you need."

## Route

Wait for selection. Map to the right command/skill:

- 1 → `/daily`
- 2 → `obsidian-media` skill (or `/media`)
- 3 → ask for the thought, write it to `Inbox/<short-slug>.md`
- 4 → `/research`
- 5 → `/brainstorm`
- 6 → ask about the project, create note from `Templates/Project Template.md` in `Projects/`
- 7 → `obsidian-maintain` skill
- 8 → `/vault-onboard`

If the user describes something in natural language instead of picking a number, route to the closest match. If nothing fits, set it up ad hoc.

## Loop

After completing an option: "Want to do something else, or are you good?"

End on user dismissal. Don't re-summarize.
