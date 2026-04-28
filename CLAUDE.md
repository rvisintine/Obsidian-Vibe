# Personal Life Vault — Claude Instructions

Starter Obsidian vault for personal knowledge management. When working in this vault, follow the conventions below.

## Folder Structure

| Folder | Purpose |
|--------|---------|
| `Inbox/` | Quick capture — process regularly into proper folders |
| `Media/` | All media notes (books, movies, shows, games, anime, manga) — flat, filtered by Bases |
| `Projects/` | Project notes and kanban boards |
| `Daily/` | Daily notes |
| `Notes/` | General notes and thoughts |
| `Categories/` | Hub pages with embedded Base views (Books.md, Movies.md, etc.) |
| `Templates/` | Note templates and `.base` view files |
| `Attachments/` | Images, cover art, and other media |
| `References/` | External reference material |
| `Recipes/` | Recipe notes |
| `Trips/` | Trip/travel notes |
| `People/` | Contact and people notes |
| `Meetings/` | Meeting notes |
| `Resources/` | Vault resources (skills, configs) |

## Naming Conventions

- **Media notes**: `Title (Type).md` — e.g., `Dark Matter (Book).md`, `Dark Matter (Show).md`
- **Project notes**: `Project Name.md`
- **Daily notes**: Obsidian's daily note format in `Daily/`
- **People**: `First Last.md`

## Template Schemas

### Book (`Templates/Book Template.md`)
```yaml
categories: ["[[Books]]"]
author: []        # list of author names
cover:            # URL to cover image
genre: []         # e.g., [sci-fi, thriller]
pages:            # page count
isbn:
isbn13:
year:             # publication year
rating:           # personal 1-10 rating
status:           # want-to-read | reading | read
finished:         # date finished reading
synopsis:         # brief plot summary
topics: []
created:          # auto-filled
last:
via: ""
```

### Movie (`Templates/Movie Template.md`)
```yaml
categories: ["[[Movies]]"]
cover:            # URL to cover/poster image
genre: []
director:
cast: []
runtime:          # in minutes
rating:           # personal 1-10 rating
status:           # want-to-watch | watched
synopsis:
year:
last:             # date last watched
imdbId:
via:
```

### Show (`Templates/Show Template.md`)
```yaml
categories: ["[[Shows]]"]
genre: []
year:             # premiere year
cast: []
rating:           # personal 1-10 rating
status:           # want-to-watch | watching | watched | dropped
seasons:          # number of seasons
network:          # streaming service or network
synopsis:
created:
last:
```

### Project (`Templates/Project Template.md`)
```yaml
categories: ["[[Projects]]"]
type:             # development | video-channel | video-idea | other
org: []
repo:             # filesystem path to project directory
description:      # one-line description
start:            # date started
year:
url:              # project URL if applicable
status:           # active | paused | idea | completed
```

### Video Channel (`Templates/Video Channel Template.md`)
```yaml
categories: ["[[Projects]]"]
type: video-channel
platform:         # TikTok | YouTube | Instagram
handle:           # @username
tools: []         # e.g., [Kling AI, CapCut, Premiere Pro]
content-type:     # e.g., AI ASMR, horror narration
repo:             # filesystem path
description:
start:
year:
url:
status:           # active | paused | idea | completed
```

### Recipe (`Templates/Recipe Template.md`)
```yaml
categories: ["[[Recipes]]"]
cuisine:
type: []
ingredients:
author: []
url:
rating:
created:
last:
```

## Cross-Linking Rules

- When creating media notes, always check for related items and add `[[wikilinks]]`:
  - Book adaptations: link book ↔ movie/show (e.g., `Dark Matter (Book)` ↔ `Dark Matter (Show)`)
  - Same author/director: mention in Thoughts section
  - Sequels/series: link between entries
- Use `[[Author Name]]` links in author fields when the person has their own note
- Project notes should link to related projects where applicable

## Media Data Sources

When populating media notes:
1. **Use Claude's built-in knowledge first** for well-known titles
2. **Web search on Amazon** for books and movies (covers, metadata)
3. **anidb.net** for anime and manga
4. Always populate: title, author/director, year, genre, synopsis, cover image URL
5. Save cover images to `Attachments/` and reference with `![[filename]]`

## Project Directories

- Configure in your global Claude config: where development projects live (e.g., `~/development/`), video projects, etc.
- When syncing projects, scan those directories for project folders.

## Skills & Commands

Custom skills live in `Resources/Skills/` and are exposed to Claude Code via the `.claude/skills` symlink. Slash commands live in `.claude/commands/`.

### Skills (always-on, natural-language triggered)
- **obsidian-media** — media intake: "I just finished Dark Matter", "add Inception to watchlist"
- **obsidian-status** — status queries + archive: "what am I reading?", "pull up X", "archive Y", "drop Z"
- **obsidian-maintain** — vault hygiene: broken links, orphans, missing properties

### Slash commands
- `/vault-onboard` — first-run interview, populates `## About Me` in this file
- `/what-now` — vault menu launcher (capture, plan, maintain)
- `/daily` — brain dump → structured daily note with carry-forward open items
- `/research` — produce a research brief saved to `References/`
- `/brainstorm` — guided questions → one concrete next action
- `/media` — alias for media intake skill
- `/maintain` — alias for maintenance skill

### Configs
Per-skill configs live in `Resources/Config/`:
- `daily.md` — daily-notes template, folder, behaviors
- `research.md` — research brief structure and defaults

Configs are created on first run of `/daily` or `/research`. Edit anytime.
