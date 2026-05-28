# Scheduling

## Purpose
Set up CronCreate-based recurring reminders for morning briefing, evening reflection, weekly review, and inbox triage.

## Workflow

### Step 1: List Existing Schedules
Run CronList to show any existing cron jobs. If any personal-secretary jobs exist, show their status.

### Step 2: Offer Default Schedule
Use AskUserQuestion to present default schedule options (multi-select):

1. **Morning Briefing** — Weekdays at configured wake-up time (default: 7:57 AM)
2. **Evening Reflection** — Weekdays at configured wind-down time (default: 9:03 PM)
3. **Weekly Review** — Sunday at 7:23 PM
4. **Inbox Triage Reminder** — Daily at 2:07 PM

If profile.md has working_hours set, adjust morning/evening times accordingly.

### Step 3: Create Cron Jobs
For each selected schedule, use CronCreate:

```
# Morning Briefing (weekdays)
CronCreate: cron="57 7 * * 1-5", prompt="/personal-secretary morning"

# Evening Reflection (weekdays)
CronCreate: cron="3 21 * * 1-5", prompt="/personal-secretary evening"

# Weekly Review (Sunday)
CronCreate: cron="23 19 * * 0", prompt="/personal-secretary review weekly"

# Inbox Triage (daily)
CronCreate: cron="7 14 * * *", prompt="/personal-secretary triage"
```

Use off-peak minutes (e.g., :57, :03, :23, :07) to avoid server contention.

### Step 4: Confirm
List all created schedules and their next run times.
Remind the user: "定时提醒会在每个会话中生效，无需额外配置。"

### Step 5: Custom Schedule
If the user wants a custom schedule, let them specify:
- Subcommand to run (morning/evening/triage/review)
- Cron expression or natural language ("every Monday at 8am")
- Whether recurring or one-shot

## Notes
- CronCreate jobs live only in the current Claude session. They expire after 7 days for recurring jobs, or on next fire for one-shot jobs.
- For persistent scheduling across sessions, the user can use the `schedule` skill (remote triggers) which supports durable cron jobs.
- If the user needs schedules to survive session restarts, recommend: `/schedule create` with the same prompts.

## Timezone
Use the timezone from `$VAULT/profile.md`. If not set, default to Asia/Shanghai (UTC+8).
