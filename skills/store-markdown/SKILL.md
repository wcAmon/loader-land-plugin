---
name: store-markdown
description: Store and share markdown files (CLAUDE.md templates, skills, documentation) on loader.land. Use when the user wants to share their CLAUDE.md, publish a skill, or store any markdown file permanently for others to access.
---

# Store Markdown on loader.land

Help users store and share markdown files permanently on loader.land's public gallery.

## When to use

- User wants to share their CLAUDE.md template
- User wants to publish a custom skill or command
- User wants to store documentation for public access
- User says "upload to loader.land" or "share this template"

## Step 1: Read the file

Read the markdown file the user wants to share. This could be:
- A CLAUDE.md file in their project
- A skill file from `~/.claude/commands/` or `~/.claude/skills/`
- Any markdown content they provide

## Step 2: Gather metadata

Ask the user:
1. **Filename**: What should this file be called? (e.g., `python-best-practices.md`)
2. **Purpose**: Brief description of what this file does
3. **Install path** (optional): Where should others install this? (e.g., `~/.claude/commands/`)

## Step 3: Upload

```bash
curl -X POST https://move.loader.land/md \
  -H "Content-Type: application/json" \
  -d '{
    "content": "[FILE_CONTENT]",
    "metadata": {
      "filename": "[FILENAME]",
      "purpose": "[PURPOSE]",
      "install_path": "[INSTALL_PATH]"
    }
  }'
```

## Step 4: Share the result

The API returns a unique code. Tell the user:

- **Share code**: `[CODE]`
- **Direct link**: `https://move.loader.land/md/[CODE]`
- **Raw content**: `https://move.loader.land/md/[CODE]/raw`
- **Gallery**: `https://move.loader.land/gallery`

Others can install this template with:
```bash
curl -s https://move.loader.land/md/[CODE]/raw -o [install_path]/[filename]
```
