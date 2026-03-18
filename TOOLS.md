# TOOLS.md - Local Notes

Skills define _how_ tools work. This file is for _your_ specifics — the stuff that's unique to your setup.

## What Goes Here

Things like:

- Camera names and locations
- SSH hosts and aliases
- Preferred voices for TTS
- Speaker/room names
- Device nicknames
- Anything environment-specific

## Examples

```markdown
### Cameras

- living-room → Main area, 180° wide angle
- front-door → Entrance, motion-triggered

### SSH

- home-server → 192.168.1.100, user: admin

### TTS

- Preferred voice: "Nova" (warm, slightly British)
- Default speaker: Kitchen HomePod
```

## Why Separate?

Skills are shared. Your setup is yours. Keeping them apart means you can update skills without losing your notes, and share skills without leaking your infrastructure.

---

## Skill Installation Rules

### 查找技能优先级
1. **优先使用 `find-skills`**（`npx skills find`）查找和安装技能
2. ClawHub（`clawhub`）作为备选，不优先使用

### 安装路径
- 通过 `find-skills` 安装的技能，必须安装到 workspace 的 skills 目录：`~/.openclaw/workspace/skills/`
- 安装命令示例：`npx skills add <owner/repo@skill> -g -y`
- 安装后如果默认路径不在 workspace/skills/，需要手动复制过去：`cp -r ~/.agents/skills/<name> ~/.openclaw/workspace/skills/<name>`

---

Add whatever helps you do your job. This is your cheat sheet.
