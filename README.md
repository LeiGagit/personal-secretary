# Personal Secretary — Claude Code Skill

A comprehensive personal life management skill for Claude Code, serving as your AI secretary for daily operations, life planning, task management, personal CRM, and periodic reviews.

## Features

- **Daily Management**: Morning briefing, evening reflection (Franklin-style), daily planning with time-blocking
- **4-Color Task System**: Red (personal attention) / Yellow (needs review) / Green (auto-delegated) / Black (deferred)
- **Quick Capture**: Instantly capture thoughts and ideas to an inbox for later triage
- **Life Planning**: Vision setting, annual goals, quarterly OKRs with progress tracking
- **Periodic Reviews**: Structured weekly, monthly, and quarterly review workflows
- **Personal CRM**: Contact profiles, interaction logging, follow-up reminders
- **Decision Records**: Structured decision logging with review dates for learning from past choices
- **Habit Tracking**: Define habits, daily logging, streak tracking, trend analysis
- **Dashboard**: Master overview of all active areas
- **Scheduling**: Cron-based morning/evening/weekly reminders

## Installation

```bash
# Clone into your Claude Code skills directory
git clone https://github.com/YOUR_USERNAME/personal-secretary.git ~/.claude/skills/personal-secretary
```

Or manually copy the `personal-secretary/` directory into `~/.claude/skills/`.

## Setup

After installation, run:

```
/personal-secretary setup
```

This will:
1. Ask for your Obsidian vault path (or create a new directory)
2. Initialize the data directory structure
3. Copy templates to your vault
4. Collect your profile (name, timezone, working hours)

## Data Storage

All data is stored as Markdown files in your Obsidian vault (or any directory you choose):

```
vault/
  0-Inbox/          Quick-capture items awaiting triage
  1-Daily/          Daily notes, morning briefings, evening reflections
  2-Tasks/          Active task files (one per task)
  3-Projects/       Multi-task project plans
  4-CRM/            Contact profiles and interaction logs
  5-Decisions/      Decision records
  6-Reviews/        Weekly/monthly/quarterly review documents
  7-Planning/       Vision, annual goals, quarterly goals
  8-Habits/         Habit definitions and daily logs
  9-Templates/      Note templates (synced from skill)
  99-Archive/       Completed or dormant items
  Dashboard.md      Master index
```

## Commands

| Command | Description |
|---------|-------------|
| `/ps setup` | First-run initialization |
| `/ps morning` | Morning briefing with MITs |
| `/ps evening` | Franklin-style evening reflection |
| `/ps plan` | Daily planning with time-blocking |
| `/ps capture <text>` | Quick capture to inbox |
| `/ps triage` | Process inbox items |
| `/ps task add/list/complete` | Task management with 4-color priority |
| `/ps vision` | Life vision and annual/quarterly goals |
| `/ps review weekly/monthly/quarterly` | Periodic reviews |
| `/ps crm add/list/followups` | Personal CRM |
| `/ps decide log/list/review` | Decision records |
| `/ps habit define/log/review` | Habit tracking |
| `/ps dashboard` | Master overview dashboard |
| `/ps schedule` | Configure auto-reminders |

## 4-Color Task Priority System

| Color | Meaning | Rule |
|-------|---------|------|
| Red | Personal attention required | Max 5 active |
| Yellow | 80% done, needs review/feedback | Must have blocker field |
| Green | Auto-delegated or routine | Batch, review weekly |
| Black | Deferred / not urgent | Auto-flagged if stale >2 weeks |

## Configuration

User-specific configuration is stored at `~/.claude/personal-secretary.json`:

```json
{
  "vault_path": "/path/to/your/obsidian/vault",
  "skill_path": "~/.claude/skills/personal-secretary",
  "setup_date": "2026-05-28"
}
```

## Requirements

- Claude Code CLI
- An Obsidian vault (recommended) or any directory for data storage

## Inspiration

This skill integrates ideas from:
- [claude-chief-of-staff](https://github.com/mimurchison/claude-chief-of-staff) — Executive assistant workflows
- [life-system](https://github.com/davidhariri/life-system) — Plain-text life OS
- [OpenPaw](https://github.com/daxaur/openpaw) — Multi-domain skill suite
- [Friday](https://github.com/missingus3r/friday-showcase) — Autonomous AI assistant
- [workplanner](https://github.com/melek/workplanner) — Daily work planning

## License

MIT
