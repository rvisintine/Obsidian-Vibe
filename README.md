# Obsidian Vibe — Personal Life Vault Template

An opinionated starter [Obsidian](https://obsidian.md) vault for personal knowledge management. Capture and organize media, projects, recipes, people, trips, daily notes, and meetings — backed by typed templates and live [Base](https://help.obsidian.md/bases) views.

Designed to pair with [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) for natural-language note creation and vault maintenance.

## What's Inside

- **Typed templates** for 50+ note kinds (books, movies, shows, games, recipes, people, projects, trips, meetings, journal entries, etc.) under `Templates/`
- **Base views** (`.base` files) under `Templates/Bases/` that filter and group notes by category
- **Category hubs** in `Categories/` that embed Base views — e.g., `Books.md`, `Movies.md`, `Recipes.md`
- **Skills** for Claude Code under `Resources/Skills/`:
  - `obsidian-media` — natural-language media intake (e.g., "I just finished Dark Matter")
  - `obsidian-maintain` — vault hygiene (broken links, orphans, missing properties)
- **Quick capture** via `Inbox/` with a Dataview query for triage
- **CLAUDE.md** documenting folder conventions, naming rules, and template schemas for AI assistants

## Folder Map

| Folder | Purpose |
|--------|---------|
| `Inbox/` | Quick capture — process regularly |
| `Daily/` | Daily notes |
| `Notes/` | General notes |
| `Projects/` | Project notes and kanban boards |
| `Media/` | Books, movies, shows, games, anime, manga (flat, filtered by Bases) |
| `Recipes/` | Recipe notes |
| `People/` | Contacts |
| `Trips/` | Travel notes |
| `Meetings/` | Meeting notes |
| `References/` | External reference material |
| `Categories/` | Hub pages embedding Base views |
| `Templates/` | Note templates (`.md`) and Base files (`.base`) |
| `Attachments/` | Cover art, images, media files |
| `Resources/Skills/` | Claude Code skills synced via Obsidian |

## Naming Conventions

- **Media notes:** `Title (Type).md` — e.g., `Dark Matter (Book).md`, `Dark Matter (Show).md`
- **Project notes:** `Project Name.md`
- **People:** `First Last.md`
- **Daily notes:** Obsidian's daily-note format under `Daily/`

## Getting Started

1. Clone or download this repo into your Obsidian vault location.
2. Open the folder in Obsidian.
3. Install community plugins as desired (Bases, Dataview, Templater).
4. Customize `CLAUDE.md` template schemas to taste.
5. Drop a thought into `Inbox/` to capture quickly; process it into the right folder later.
6. Browse `Categories/` for live filtered views of each note type.

## Using With Claude Code

The vault includes two skills that activate when you run Claude Code in this directory:

- `/media` — natural-language media intake. Example: *"I just finished reading Project Hail Mary"* → creates `Project Hail Mary (Book).md` with cover, author, ISBN, synopsis pre-filled.
- `/maintain` — vault health check. Fixes broken links, orphaned notes, inconsistent properties.

`CLAUDE.md` defines the conventions Claude follows when creating or editing notes in this vault.

## Cross-Linking

When creating media notes, related items are automatically linked:

- Book ↔ adaptation (e.g., `Dark Matter (Book)` ↔ `Dark Matter (Show)`)
- Author/director get their own notes when worth tracking
- Sequels and series link between entries

## What's Not Tracked

Listed in `.gitignore`:

- macOS / Windows / Linux OS noise (`.DS_Store`, `Thumbs.db`, etc.)
- Obsidian per-machine state (`.obsidian/workspace`, cache)
- Claude Code local settings (`.claude/settings.local.json`)
- Editor / IDE files (`.vscode/`, `.idea/`)

The `.obsidian/` config folder itself is not committed by default — fork and add it if you want to share plugin/theme/hotkey config across machines.

## License

Personal use template — fork freely.
