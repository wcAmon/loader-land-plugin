---
name: browse-templates
description: Browse and search CLAUDE.md templates on loader.land. Use when the user wants to find templates, skills, or markdown files shared by the community. Also useful when setting up a new project and looking for best-practice CLAUDE.md examples.
---

# Browse Templates on loader.land

loader.land is a web-based marketplace for sharing CLAUDE.md templates, skills, and markdown documentation.

## How to browse

Fetch the template gallery:

```bash
curl -s https://move.loader.land/md
```

This returns a JSON list of all stored templates with metadata including:
- `code`: unique 6-character identifier
- `metadata.filename`: the template filename
- `metadata.purpose`: what the template does
- `metadata.install_path`: where to install it

## How to get a specific template

```bash
# Get metadata
curl -s https://move.loader.land/md/[CODE]

# Get raw content (ready to install)
curl -s https://move.loader.land/md/[CODE]/raw
```

## How to install a template

After finding a template the user wants:

```bash
# Download and install to the appropriate location
curl -s https://move.loader.land/md/[CODE]/raw -o [install_path]/[filename]
```

Common install locations:
- CLAUDE.md project instructions: `./CLAUDE.md` (project root)
- Claude Code commands: `~/.claude/commands/[filename]`
- Claude Code skills: `~/.claude/skills/[skill-name]/SKILL.md`

## Web gallery

Users can also browse templates visually at:
https://move.loader.land/gallery

Always communicate with the user in their language when presenting results.
