# Obsidian Vibe — Personal Life Vault Template

An opinionated starter [Obsidian](https://obsidian.md) vault for personal knowledge management. Capture and organize media, projects, recipes, people, trips, daily notes, and meetings — backed by typed templates and live [Base](https://help.obsidian.md/bases) views.

The vault structure, templates, and Bases work standalone. AI-assistant integration is included for [Claude Code](https://docs.claude.com/en/docs/claude-code/overview) out of the box, and adapts to GitHub Copilot, Cursor, Gemini Code Assist, Aider, and other tools — see [Adapting to Other LLMs](#adapting-to-other-llms).

## What's Inside

- **Typed templates** for 50+ note kinds (books, movies, shows, games, recipes, people, projects, trips, meetings, journal entries, etc.) under `Templates/`
- **Base views** (`.base` files) under `Templates/Bases/` that filter and group notes by category
- **Category hubs** in `Categories/` that embed Base views — e.g., `Books.md`, `Movies.md`, `Recipes.md`
- **Skills** under `Resources/Skills/` — markdown procedures usable by any AI assistant:
  - `obsidian-media` — natural-language media intake (e.g., "I just finished Dark Matter")
  - `obsidian-status` — status queries and archive ("what am I reading?", "archive X")
  - `obsidian-maintain` — vault hygiene (broken links, orphans, missing properties)
- **Slash commands** for Claude Code under `.claude/commands/` — onboarding, daily notes, research briefs, brainstorm, menu launcher
- **Quick capture** via `Inbox/` with a Dataview query for triage
- **`CLAUDE.md`** documenting folder conventions, naming rules, and template schemas for AI assistants (works as instructions for any LLM, not just Claude)

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
| `Resources/Skills/` | AI-assistant skills (markdown procedures) |
| `Resources/Config/` | Per-skill configs (daily notes, research) — created on first use |

## Naming Conventions

- **Media notes:** `Title (Type).md` — e.g., `Dark Matter (Book).md`, `Dark Matter (Show).md`
- **Project notes:** `Project Name.md`
- **People:** `First Last.md`
- **Daily notes:** Obsidian's daily-note format under `Daily/`

## Getting Started

1. **Clone the repo** into your Obsidian vaults folder (or wherever you keep them).
2. **Open it in Obsidian.** Trust the vault when prompted.
3. **Enable plugins.** Bases is core in modern Obsidian; install Dataview and Templater from Community Plugins if you want the daily note query and templater syntax to work.
4. **Personalize the vault.** Pick one:
   - **With Claude Code:** run `/vault-onboard` from the vault directory. A short interview adds an `## About Me` section to `CLAUDE.md` so the assistant knows your name, household, interests, food rules, and communication preferences across every session.
   - **With another LLM:** edit `CLAUDE.md` directly and add your own `## About Me` section near the top — see [Adapting to Other LLMs](#adapting-to-other-llms) for setup.
   - **Skip:** the vault works fine without personalization; only AI-assistant context is affected.
5. **Set up the daily-notes workflow** (optional but recommended). Run `/daily` once to choose a template and folder; afterward, just say *"log today"* or *"log [what I did]"* and your assistant will create/update `Daily/YYYY-MM-DD.md`.
6. **Start using it.** Drop thoughts into `Inbox/` for quick capture, browse `Categories/` for live filtered views, run `/what-now` anytime you don't know where to begin.

## Using With Claude Code

Run Claude Code in the vault directory and you get a set of skills (always-on, natural-language) and slash commands:

### Skills

- **obsidian-media** — *"I just finished reading Project Hail Mary"* → creates `Project Hail Mary (Book).md` with cover, author, ISBN, synopsis, and a 7-question mini-review.
- **obsidian-status** — *"what am I reading?"*, *"pull up Severance"*, *"archive that project"* → status queries + frontmatter mutations on existing notes.
- **obsidian-maintain** — vault health check: broken links, orphans, inconsistent properties, missing fields.

### Slash commands

- `/vault-onboard` — first-run interview that personalizes `CLAUDE.md` with your profile (name, household, interests, food rules, communication style, ground rules).
- `/what-now` — vault menu launcher; pick capture / plan / maintain or just describe what you need.
- `/daily` — brain dump → structured daily note with carry-forward of unfinished `- [ ]` items from the prior day. First run sets up the config.
- `/research <topic>` — produce a research brief saved to `References/` with sources, findings, and recommendations. First run sets up defaults.
- `/brainstorm` — guided 2–3 questions → one concrete next action, mapped to a vault operation.

`CLAUDE.md` defines the conventions Claude follows when creating or editing notes in this vault. Per-skill configs live in `Resources/Config/` and are generated on first use.

## Adapting to Other LLMs

The vault is structured so the **content layer** (templates, Bases, folder conventions, skill procedures) is platform-agnostic markdown. Only the slash-command layer is Claude Code–specific.

### What's portable

| Asset | Format | Works with |
|---|---|---|
| `CLAUDE.md` | Plain markdown | Any LLM that reads instruction files |
| `Resources/Skills/*/SKILL.md` | Plain markdown procedures | Any agent — paste into a system prompt or rules file |
| Templates, Bases, folder structure | Pure Obsidian | Any tool, no AI required |
| `Resources/Config/*.md` | Plain markdown | Any LLM (read + follow) |

### What's Claude Code–only

- Slash commands in `.claude/commands/` (`/vault-onboard`, `/daily`, `/research`, etc.)
- Auto-loading of `CLAUDE.md` and `SKILL.md` files

For other tools, invoke the same workflows by reading the corresponding skill or command file and asking the assistant to follow it. E.g., *"Read `.claude/commands/daily.md` and run the repeat-run flow with this brain dump: …"*

### Setup per tool

| Tool | How to wire it up |
|---|---|
| **Claude Code** | Works out of the box. `CLAUDE.md`, skills, and slash commands auto-load. |
| **GitHub Copilot Chat** | Create `.github/copilot-instructions.md` symlinked or copied from `CLAUDE.md`. Copilot will treat it as workspace context. |
| **Cursor** | Add a `.cursorrules` file (or `.cursor/rules/vault.mdc`) referencing `CLAUDE.md`, or copy its contents in. |
| **Gemini Code Assist** | Add `.idx/airules.md` (in IDX) or paste `CLAUDE.md` into Gemini's chat as a system prompt. |
| **Aider** | Add a `CONVENTIONS.md` symlink to `CLAUDE.md` and set `read: CLAUDE.md` in `.aider.conf.yml`. |
| **OpenAI Codex CLI / generic agents** | Symlink `AGENTS.md → CLAUDE.md` (the emerging cross-tool standard). |
| **ChatGPT / generic chat** | Paste `CLAUDE.md` into a Project's instructions or the system prompt. Reference skill files when invoking workflows. |

A one-shot symlink that covers most modern agent-style tools:

```bash
ln -s CLAUDE.md AGENTS.md
```

### Caveats for non-Claude tools

- **No auto-onboarding.** Without `/vault-onboard`, edit `CLAUDE.md` by hand to add your `## About Me` section.
- **No auto-config.** `/daily` and `/research` write configs to `Resources/Config/` on first run; with another tool, create those files manually using the structures shown in `.claude/commands/daily.md` and `.claude/commands/research.md` as references.
- **Status/archive and media intake** still work — point the assistant at `Resources/Skills/obsidian-status/SKILL.md` or `obsidian-media/SKILL.md` and ask it to follow the procedure.

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

If you wire up another tool (e.g., add a `.cursorrules`, `.aider.conf.yml`, or `AGENTS.md` symlink), commit those alongside `CLAUDE.md` so collaborators using the same tool inherit them.

The `.obsidian/` config folder itself is not committed by default — fork and add it if you want to share plugin/theme/hotkey config across machines.

## License

Personal use template — fork freely.
