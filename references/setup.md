# Setup: First-Run Initialization

## Overview
Initialize the configuration and Obsidian vault with the secretary data structure.
This is idempotent — running it again will not overwrite user data.

## Workflow

### Step 0: Check Existing Config
Check if `~/.claude/personal-secretary.json` exists. If it does, read `vault_path` and confirm with the user before re-initializing.

### Step 1: Configure Vault Path
Use AskUserQuestion to ask:
"What is the path to your Obsidian vault?"

If the user has an Obsidian vault at a common location, suggest it.
If the user doesn't use Obsidian, ask for any directory where they want to store secretary data.

Save the configuration:
```json
{
  "vault_path": "/path/to/vault",
  "skill_path": "~/.claude/skills/personal-secretary",
  "setup_date": "YYYY-MM-DD"
}
```
Write to `~/.claude/personal-secretary.json`.

All subsequent operations use `$VAULT` = the configured `vault_path`.

### Step 2: Verify Vault
Check if the configured vault directory exists. If not, ask if it should be created.
Abort if the user declines.

### Step 3: Create Data Directories
Create these subdirectories under `$VAULT` if they don't exist:
```
0-Inbox/
1-Daily/
2-Tasks/
3-Projects/
4-CRM/
5-Decisions/
6-Reviews/
7-Planning/
8-Habits/
9-Templates/
99-Archive/
```

### Step 4: Copy Templates
Copy all `.md` files from `$SKILL/templates/` to `$VAULT/9-Templates/`.
For each template that already exists in the vault, use AskUserQuestion to confirm overwrite.

### Step 5: Create Dashboard.md
Create `$VAULT/Dashboard.md` with a starter dashboard that includes:
- Today's Focus section with 3 MIT slots
- Active Tasks by priority (red/yellow/green/black)
- Upcoming Follow-ups
- This Week's Habits
- Current Quarter Goals link
- Pending Decisions
- Quick Links to all major sections (Inbox, Daily Notes, Tasks, Contacts, Decisions, Vision)

Refer to `$VAULT/9-Templates/daily-note.md` for formatting conventions.

### Step 6: Collect User Profile
Use AskUserQuestion to collect:
1. Preferred name / how to address you
2. Timezone (for scheduling, e.g., Asia/Shanghai)
3. Typical working hours (e.g., 9:00-18:00)
4. Location (optional, for weather in morning briefing)
5. Default language preference (Chinese/English/Mixed)

Save to `$VAULT/profile.md`:
```markdown
---
name: "{{NAME}}"
timezone: "{{TIMEZONE}}"
working_hours: "{{HOURS}}"
location: "{{LOCATION}}"
language: "{{LANGUAGE}}"
setup_date: "{{TODAY}}"
---
```

### Step 7: Confirm
Report what was created and suggest next steps:
- Run `/personal-secretary vision` to set up life vision and goals
- Run `/personal-secretary schedule` to configure daily/weekly reminders
- Run `/personal-secretary capture` to start capturing thoughts
