---
name: download-settings
description: Download and restore AI assistant settings from loader.land. Use when the user has a 6-character code from a previous backup and wants to restore their settings on this machine.
---

# Download Settings from loader.land

Help users restore their AI assistant settings using a 6-character transfer code.

## Step 1: Get the code

Ask the user for their 6-character transfer code. They got this code when they uploaded their settings on another machine.

## Step 2: Download the backup

```bash
curl -s https://move.loader.land/download/[CODE] -o /tmp/restore.tar.gz
```

If the code is invalid or expired (24h limit), the API returns an error.

## Step 3: Extract and preview

```bash
mkdir -p /tmp/restore
cd /tmp/restore && tar xzf /tmp/restore.tar.gz
ls -la /tmp/restore/tool-config/
```

**IMPORTANT**: Show the user what files will be restored and ask for confirmation before overwriting anything.

## Step 4: Restore (with user confirmation)

### Claude Code
```bash
# Restore settings files
cp /tmp/restore/tool-config/settings.json ~/.claude/ 2>/dev/null
cp /tmp/restore/tool-config/settings.local.json ~/.claude/ 2>/dev/null
cp /tmp/restore/tool-config/keybindings.json ~/.claude/ 2>/dev/null
cp /tmp/restore/tool-config/.clauderc ~/.claude/ 2>/dev/null
cp /tmp/restore/tool-config/.mcp.json ~/.claude/ 2>/dev/null

# Restore commands and skills
cp -r /tmp/restore/tool-config/commands/ ~/.claude/commands/ 2>/dev/null
cp -r /tmp/restore/tool-config/skills/ ~/.claude/skills/ 2>/dev/null
```

### Codex
```bash
cp /tmp/restore/tool-config/config.json ~/.codex/ 2>/dev/null
cp -r /tmp/restore/tool-config/skills/ ~/.codex/skills/ 2>/dev/null
```

## Step 5: Cleanup

```bash
rm -rf /tmp/restore /tmp/restore.tar.gz
```

Tell the user to restart their AI assistant to apply the restored settings.
