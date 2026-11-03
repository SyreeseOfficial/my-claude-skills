# my-claude-skills

Backup of my custom [Claude Code](https://claude.com/claude-code) skills.

## Skills

| Skill | What it does |
|-------|--------------|
| [`distill`](distill/SKILL.md) | Makes a text file more concise without losing any detail. |
| [`podcasts`](podcasts/SKILL.md) | Organizes my Obsidian podcast tracker and creates missing episode notes. |

## Install

Copy a skill folder into `~/.claude/skills/`:

```bash
cp -r distill ~/.claude/skills/
```

## Back up a new skill

```bash
cp -r ~/.claude/skills/<name> .
git add -A && git commit -m "Add <name>" && git push
```
