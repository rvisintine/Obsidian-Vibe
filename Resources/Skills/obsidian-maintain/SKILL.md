---
name: obsidian-maintain
description: Run vault maintenance — fix missing links, orphaned notes, inconsistent properties, and empty fields. Use when user says /maintain, "tidy up the vault", "fix my notes", "check for issues", or asks about vault health.
---

# Vault Maintenance

On-demand vault cleanup and improvement. Scan notes, identify issues, propose fixes, apply with approval.

## Process

1. **Scan the vault** — read all notes in content folders:
   - `Media/`, `Projects/`, `Daily/`, `Notes/`, `Recipes/`, `Trips/`, `People/`
   - Skip `Templates/`, `Categories/`, `References/`, `.obsidian/`, `.claude/`

2. **Check for issues** in this priority order:

### Missing Cross-Links
- Books by the same author should mention each other
- Media adaptations (book ↔ movie/show with same title) should be linked
- Projects using the same technology should be linked
- People mentioned in multiple notes should be linked

### Inconsistent Properties
- Status field empty on media notes (should have a value)
- Missing `year:` on media with known dates
- Missing `genre:` on media
- Missing `author:`/`director:` on media
- Date fields in wrong format (should be YYYY-MM-DD)

### Orphaned Notes
- Notes with no backlinks and no outgoing links
- Notes not in any category

### Formatting Issues
- Frontmatter syntax errors
- Empty body sections (## Thoughts with just `-`)
- Missing categories link

3. **Report findings** — present a summary:
   ```
   ## Vault Health Report

   ### Issues Found
   - X missing cross-links
   - X incomplete properties
   - X orphaned notes
   - X formatting issues

   ### Details
   [list each issue with the file and what needs fixing]

   ### Recommended Fixes
   [list proposed changes]
   ```

4. **Apply fixes** — after user approval, make the changes

## What NOT to Change
- Don't modify Templates/ or base files
- Don't change user's personal thoughts or ratings
- Don't add properties that aren't in the template schema
- Don't delete any notes
- Don't change filenames without asking
