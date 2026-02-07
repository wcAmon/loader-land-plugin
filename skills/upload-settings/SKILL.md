---
name: upload-settings
description: Upload and migrate AI assistant settings to loader.land. Use when the user wants to backup their settings, transfer configuration to another machine, or share their setup. Supports Claude Code, Codex, and OpenClaw configurations.
---

# Upload Settings to loader.land

Help users backup and migrate their AI assistant settings using loader.land's temporary transfer service.

## Step 1: Identify the tool

Detect which AI assistant is running:
- **Claude Code**: check for `~/.claude/` directory
- **Codex**: check for `~/.codex/` directory
- **OpenClaw**: check for `~/.openclaw/` or `~/.moltbot/` directory

## Step 2: Collect settings files

### Claude Code
```bash
mkdir -p /tmp/backup/tool-config
cp ~/.claude/settings.json /tmp/backup/tool-config/ 2>/dev/null
cp ~/.claude/settings.local.json /tmp/backup/tool-config/ 2>/dev/null
cp ~/.claude/keybindings.json /tmp/backup/tool-config/ 2>/dev/null
cp ~/.claude/.clauderc /tmp/backup/tool-config/ 2>/dev/null
cp ~/.claude/.mcp.json /tmp/backup/tool-config/ 2>/dev/null
cp -r ~/.claude/commands/ /tmp/backup/tool-config/commands/ 2>/dev/null
cp -r ~/.claude/skills/ /tmp/backup/tool-config/skills/ 2>/dev/null
```

### Codex
```bash
mkdir -p /tmp/backup/tool-config
cp ~/.codex/config.json /tmp/backup/tool-config/ 2>/dev/null
cp -r ~/.codex/skills/ /tmp/backup/tool-config/skills/ 2>/dev/null
```

## Step 3: Create archive and upload

```bash
cd /tmp/backup && tar czf /tmp/backup.tar.gz .
curl -X POST https://move.loader.land/upload \
  -F "file=@/tmp/backup.tar.gz" \
  -F "tool_type=claude-code"
```

The response includes a **6-character code** valid for 24 hours.

**Tell the user**: "Your settings backup code is `[CODE]`. Use this code on your other machine within 24 hours to restore your settings."

## Step 4: Cleanup

```bash
rm -rf /tmp/backup /tmp/backup.tar.gz
```
