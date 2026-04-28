---
description: Guided questions to surface what's on your mind and turn it into a concrete next step
allowed-tools: Read, Write, Glob
---

Help the user discover what they're actually missing. Not open-ended — guided. Aim for one concrete next action by the end.

## Load context

Read vault root `CLAUDE.md` (especially `## About Me` if it exists). Glob the contents of `Inbox/`, `Projects/`, `Daily/` — last few items each. This grounds suggestions in actual state, not abstractions.

## Ask 2–3 guided questions

Pick 2–3 from this set, one per message. Acknowledge each answer before the next. Adapt order based on what they say.

1. "What's been rattling around in your head that you keep meaning to do something with?"
2. "What's the thing you're procrastinating on right now?"
3. "Anything you've been re-reading, re-watching, or re-thinking lately? Any pattern there?"
4. "What did you say 'I should write that down' about this week and didn't?"
5. "Is there a project you started that's been quiet for a while? Worth picking back up, or worth letting go?"
6. "Anything coming up — trip, event, decision — that you haven't started thinking about yet?"

Stop as soon as you have enough to make a concrete suggestion. Usually 2 questions, sometimes 3.

## Suggest one concrete next step

Based on answers, propose ONE specific action. Map needs to vault operations:

- **Idea or thought** → quick-capture to `Inbox/<slug>.md`
- **Procrastination on a project** → create or revive a project note in `Projects/`; suggest a 15-minute next action
- **Recurring theme / pattern** → add an evergreen note in `Notes/`
- **Topic to understand** → run `/research [topic]`
- **Trip / event coming up** → create a trip note from `Templates/Trip Template.md` in `Trips/`
- **Want-to-do media** → add to vault via `obsidian-media` skill
- **Stalled project** → ask if it should be archived (set `status: archived`) instead of guilt-tripping

Frame it as a single offer: "Sounds like [option] would help. Want me to set that up now?"

If the answer is yes, do it. If no, drop it — don't push.

## End

"Want to keep going, or head back to `/what-now`?"

End on user dismissal.
