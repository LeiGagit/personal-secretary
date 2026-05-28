---
name: personal-secretary
description: Use when the user wants to manage personal life systems — daily planning, task management with 4-color priority, habit tracking, personal CRM, decision logging, periodic reviews, quick capture, or life vision and goal setting. Supports morning briefing, evening reflection, inbox triage, and weekly/monthly/quarterly review workflows.
argument-hint: "[morning|evening|plan|capture|triage|task|vision|review|crm|decide|habit|dashboard|schedule|setup] [args]"
user-invocable: true
allowed-tools: Read, Write, Edit, Glob, Grep, AskUserQuestion, CronCreate, CronList, CronDelete, TaskCreate, TaskUpdate, WebFetch, Bash
model: sonnet
---

# Personal Secretary

Your personal AI secretary for daily operations, life planning, and task management.
All data stored in the Obsidian vault for full user ownership and interoperability.

## Routing Table

| Subcommand | Reference File | Description |
|-----------|---------------|-------------|
| `setup` | `references/setup.md` | First-run vault initialization |
| `morning` | `references/morning-briefing.md` | Morning briefing: tasks, MITs, calendar |
| `evening` | `references/evening-reflection.md` | Franklin-style evening reflection |
| `plan` | `references/daily-planning.md` | Daily planning with time-blocking |
| `capture` | `references/quick-capture.md` | Quick capture thought/idea/task to inbox |
| `triage` | `references/inbox-triage.md` | Process and classify inbox items |
| `task` | `references/task-management.md` | Task CRUD with 4-color priority system |
| `vision` | `references/life-planning.md` | Life vision, annual/quarterly goals |
| `review` | `references/periodic-reviews.md` | Weekly, monthly, quarterly reviews |
| `crm` | `references/personal-crm.md` | Contact profiles and relationship tracking |
| `decide` | `references/decision-records.md` | Structured decision logging |
| `habit` | `references/habit-tracking.md` | Habit definitions and daily tracking |
| `dashboard` | `references/dashboard.md` | Master overview dashboard |
| `schedule` | `references/scheduling.md` | Set up CronCreate-based reminders |

## Phase 0: Parse Subcommand

Parse `$ARGUMENTS`. First word is the subcommand, remainder is args.
If no subcommand or invalid subcommand, display the routing table above as help.
If `$ARGUMENTS` is empty and no prior context, default to `dashboard`.

## Phase 1: Load Configuration

The skill stores its configuration at `~/.claude/personal-secretary.json`.
Read this file to obtain `vault_path` — the path to the user's Obsidian vault.

If the config file does not exist, the skill has not been set up.
Redirect to `/personal-secretary setup`.

The `skill_path` is the directory containing this SKILL.md file:
`~/.claude/skills/personal-secretary/`

In all reference files, the notation `$VAULT` means the configured `vault_path`.
The notation `$SKILL` means the skill installation directory.

## Phase 2: Dispatch

1. Read the corresponding reference file from `$SKILL/references/<file>.md`
2. Execute the workflow defined in that reference file
3. Return results to the user concisely

## Core Principles

- **Data belongs to the user**: Everything is Markdown in the Obsidian vault. No proprietary formats.
- **Progressive disclosure**: Morning briefing is quick. Deeper reviews are thorough. The user controls depth.
- **4-color task system**: Red (personal attention, max 5) / Yellow (needs review) / Green (auto-delegated) / Black (deferred). Detailed in `references/4-color-system.md`.
- **Human judgment boundary**: The secretary prepares and suggests, never decides or sends on the user's behalf.
- **Portable configuration**: All user-specific paths are stored in `~/.claude/personal-secretary.json`, never hardcoded in skill files.

## Quick Reference

```
/ps morning                        # Start the day
/ps evening                        # End the day
/ps capture <text>                 # Quick capture a thought
/ps task add <title>               # Create a new task
/ps task list                      # List all active tasks
/ps vision                         # View life vision and goals
/ps review weekly                  # Weekly review
/ps crm followups                  # Check follow-up reminders
/ps dashboard                      # Master overview
/ps schedule                       # Configure auto-reminders
```
