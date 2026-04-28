---
description: First-run interview that personalizes vault CLAUDE.md with who you are and what you care about
allowed-tools: Read, Write, Edit, Glob
---

One-time conversational onboarding. Adds an `## About Me` section to the vault root `CLAUDE.md` so Claude has personal context across every session.

## Detect mode

Read the vault root `CLAUDE.md`. Search for an existing `## About Me` heading.

- **Already exists** → ask: "You've already onboarded. Want to update your profile, start fresh, or cancel?"
  - Update → continue, but show current values and ask which to change
  - Fresh → continue, replace section
  - Cancel → end
- **Doesn't exist** → continue

## Interview

Ask one question per message. Acknowledge each answer before the next. Skip anything already covered. Adapt — this is a conversation, not a form.

1. **Name and how you want to be addressed.** *(So I know who I'm talking to.)*

2. **Where do you live? Anything seasonal or local I should keep in mind — climate, time zone, region?** *(Affects trip planning, recipe seasonality, daylight assumptions.)*

3. **Who's in your household? Partner, kids, pets, roommates?** *(Context for recipes, planning, gift ideas, scheduling.)*

4. **What do you do for work — at a high level?** *(Just enough to know your domain. Not for work-tracking — this vault is personal.)*

5. **What do you spend your free time on? Hobbies, sports, side projects, creative pursuits?** *(So I can connect dots between projects, media, and what you're into.)*

6. **What kinds of media do you consume most — books, shows, games, music, podcasts? Genres you gravitate to?** *(Helps me suggest connections and process media intake faster.)*

7. **Any dietary preferences, allergies, or food rules?** *(For recipes and trip dining.)*

8. **How do you want me to talk to you? Concise vs. detailed, casual vs. formal, bullets vs. prose?** *(How we collaborate, not how I represent you to others.)*

9. **Any ground rules — things I should never do without asking first?** *(E.g., never delete notes, never edit Daily/, always confirm archive.)*

10. **Anything else worth knowing on day one?** *(Catch-all.)*

**Pacing:** one question per message. Stop early if user says they're done. 5–10 exchanges total.

## Write the section

Append (or replace) an `## About Me` section in the vault root `CLAUDE.md`. Keep it under 40 lines. Use this structure:

```markdown
## About Me

- **Name:** [Name, preferred form of address]
- **Location:** [City, region, climate notes]
- **Household:** [Partner, kids, pets — names if shared]
- **Work:** [Role/domain — one line]

### Interests
[3–6 bullets: hobbies, sports, creative pursuits]

### Media Tastes
[Genres, formats, current obsessions]

### Food
[Dietary preferences, allergies, rules]

### Communication
[How Claude should write to me — concise/detailed, tone]

### Ground Rules
[Never-without-asking items, defaults to:]
- Confirm before deleting any note
- Confirm before archiving (status changes are fine to propose)
- Never overwrite Daily/ notes — append only
```

Place the section directly after the existing `# Personal Life Vault — Claude Instructions` intro paragraph, before `## Folder Structure`.

## Confirm

Show a 4–5 bullet recap of what you captured. End with:

"Profile saved to `CLAUDE.md`. Run `/what-now` anytime to set up daily notes, research workflows, or projects. Run `/vault-onboard` again to update."
