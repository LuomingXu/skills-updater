# Skills Updater

Manage, update, and discover Claude Code skills across multiple installation sources.

[中文](README.md)

## Features

- **Update Checker** - Scan installed skills and check for available updates
- **Auto-Install** - Automatically reinstall affected skills after marketplace updates
- **Skill Recommendations** - Discover trending skills from skills.sh
- **i18n Support** - Auto-detect locale (English/Chinese)

## Installation

Copy the `skills-updater` folder to your Claude Code skills directory:

```bash
cp -r skills-updater ~/.claude/skills/
```

Or install via marketplace (if available):

```bash
claude /install skills-updater@<marketplace>
```

## Quick Start

### Check for Updates

```bash
python ~/.claude/skills/skills-updater/scripts/check_updates.py
```

Output:
```
📦 Installed Skills Status
━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Up-to-date (15):
   • skill-creator@daymade-skills (1.2.2)
   ...

⬆️ Updates Available (2):
   • document-skills@anthropic-agent-skills
     Local: e5c60158 → Remote: 69c0b1a0
```

### Update Marketplace & Auto-Install

```bash
# Update marketplace and reinstall affected skills
python ~/.claude/skills/skills-updater/scripts/update_marketplace.py anthropic-agent-skills --auto-install
```

### Discover New Skills

```bash
python ~/.claude/skills/skills-updater/scripts/recommend_skills.py
```

## Language Support

Auto-detects from environment (`LANG`, `LC_ALL`), or specify manually:

```bash
# Chinese
python scripts/check_updates.py --lang zh

# English
python scripts/check_updates.py --lang en
```

## Scripts

| Script | Description |
|--------|-------------|
| `check_updates.py` | Scan and compare installed vs remote versions |
| `update_marketplace.py` | Update marketplace repos and auto-reinstall skills |
| `recommend_skills.py` | Fetch trending skills from marketplaces |
| `i18n.py` | Internationalization module |

## Documentation

See [SKILL.md](SKILL.md) for detailed documentation including:
- Complete workflow guide
- Version detection methods
- Smart merge strategy
- Error handling
- Adding new languages

## Supported Marketplaces

See [references/marketplaces.md](references/marketplaces.md) for the full list.

**Official:**
- `anthropics/skills` - Anthropic example skills
- `anthropics/claude-plugins-official` - Official plugins

**Community:**
- `daymade/claude-code-skills` - Community skills
- `obra/superpowers-marketplace` - Extended capabilities
- `skills.sh` - npx skills leaderboard

## License

MIT
