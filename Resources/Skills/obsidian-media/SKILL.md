---
name: obsidian-media
description: Add media (books, movies, shows, games, anime, manga) to the Obsidian vault from natural language input. Use when the user mentions finishing, starting, or wanting to consume any media — e.g., "I just finished reading Dark Matter", "add Inception to my watchlist", "I'm starting Demon Slayer". Also triggered by /media command.
---

# Media Intake

Add media entries to the vault from natural language input. Parse what the user said, look up metadata, create properly formatted notes.

## Process

1. **Parse input** — identify from the user's message:
   - Media type (book, movie, show, game, anime, manga)
   - Title
   - Status (read/watched/playing, want-to-read/watch/play, currently reading/watching/playing)
   - Any personal notes, rating, or thoughts
   - Multiple items if mentioned (e.g., "finished the book, going to watch the show")

2. **Look up metadata** — for each item:
   - Use your built-in knowledge for well-known titles
   - If unsure or for detailed data (cover art, cast, ISBN), use web search:
     - Amazon for books and movies
     - anidb.net for anime and manga
     - General web search as fallback
   - Required fields: title, author/director/creator, year, genre, synopsis
   - Nice to have: cover image URL, cast, page count/runtime, network/publisher

3. **Create the note** in `Media/` folder:
   - Filename: `Title (Type).md` — e.g., `Dark Matter (Book).md`
   - If title contains characters invalid for filenames, sanitize them
   - Use the appropriate template schema from `references/templates.md`
   - Fill in all metadata fields
   - Add user's personal thoughts to the `## Thoughts` section
   - Set `last:` to today's date if status is read/watched
   - Set `finished:` to today's date for books with status `read`

4. **Cross-link** — check for related items:
   - Adaptations: link book ↔ movie/show notes if both exist
   - Same creator: mention other works in vault by same author/director
   - Add wikilinks in the Thoughts section for connections

5. **Review questions** — if the media status is completed (read/watched/played):
   - After creating the note, ask the user these questions to generate a mini review:
     1. How would you rate it? (1-10)
     2. What stood out to you the most?
     3. How did you feel about the ending?
     4. Any favorite characters or moments?
     5. What's one thing you wish was different?
     6. Would you recommend it? Who would love it?
     7. How does it compare to something similar you've enjoyed?
   - Ask all 7 unless a specific question doesn't make sense for the media type (e.g., "favorite characters" for a puzzle game)
   - The user can say "skip" to any question — just move on
   - After collecting answers, write a natural first-person mini review in the `## Thoughts` section of the note
   - Update the `rating:` property if they gave one
   - Keep the review concise and authentic to how they expressed things — don't over-polish or add sentiments they didn't express
   - Skip this step entirely for want-to-read/watch/play statuses

6. **Report** — tell the user what was created, with key details

## Status Values

| Type | Statuses |
|------|----------|
| Book | `want-to-read`, `reading`, `read` |
| Movie | `want-to-watch`, `watched` |
| Show | `want-to-watch`, `watching`, `watched`, `dropped` |
| Game | `want-to-play`, `playing`, `played` |

## Cover Images

If a cover image URL is found, save the URL in the `cover:` property. If you can download the image, save it to `Attachments/` as `Title (Type) Cover.ext` and reference it in the note.

## Template Reference

Read `references/templates.md` for exact frontmatter schemas if you need a refresher. The CLAUDE.md in the vault root also has all schemas.
