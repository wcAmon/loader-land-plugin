# loader-land Plugin for Claude Code

Browse, install, and share CLAUDE.md templates via [loader.land](https://move.loader.land) — the web-based template marketplace for AI assistants.

## Features

- **Browse Templates** — Search the community gallery for CLAUDE.md templates, skills, and shared markdown files
- **Upload Settings** — Backup your Claude Code / Codex / OpenClaw configuration for transfer to another machine
- **Download Settings** — Restore settings from a 6-character transfer code
- **Store & Share** — Publish your CLAUDE.md templates and skills for others to use

## Installation

### From marketplace (recommended)

```
/plugin install loader-land@loader-land-marketplace
```

### Manual installation

```bash
claude --plugin-dir /path/to/loader-land-plugin
```

## Usage

After installation, you can:

1. **Use the slash command**: `/loader-land:loader-land` to see all available actions
2. **Let Claude auto-invoke**: Claude will automatically use these skills when relevant — for example, when you say "find a CLAUDE.md template" or "backup my settings"

### Browse templates
```
/loader-land:browse-templates
```
or simply ask: "Show me CLAUDE.md templates on loader.land"

### Upload settings
```
/loader-land:upload-settings
```
or say: "Backup my Claude Code settings"

### Download settings
```
/loader-land:download-settings
```
or say: "Restore my settings with code ABC123"

### Store markdown
```
/loader-land:store-markdown
```
or say: "Share my CLAUDE.md on loader.land"

## About loader.land

loader.land is an open-source platform for sharing AI assistant configurations. Unlike CLI sync tools, it provides a web-based gallery where anyone can discover and install CLAUDE.md templates without authentication.

- **Website**: https://move.loader.land
- **Gallery**: https://move.loader.land/gallery
- **API Docs**: https://move.loader.land/api-docs
- **Source Code**: https://github.com/wcAmon/cloud-loader
- **License**: MIT
