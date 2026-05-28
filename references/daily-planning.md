# Daily Planning

## Workflow

### Step 1: Check Today's Note
Read `$VAULT/1-Daily/YYYY-MM-DD.md`. Create from template if missing.

### Step 2: Review Context
1. List active tasks from `$VAULT/2-Tasks/`, sorted by priority
2. Check any calendar or time-sensitive items
3. Review this week's focus from the most recent weekly review in `$VAULT/6-Reviews/`

### Step 3: Set MITs
Ask the user to identify 1-3 Most Important Tasks for today.
Rules:
- At most 3 MITs — more than 3 means nothing is truly a priority
- Each MIT should be completable within the day
- MITs should align with weekly goals and quarterly objectives

### Step 4: Time-Block (Optional)
Ask if the user wants to time-block the day. If yes:
1. Ask for fixed commitments (meetings, appointments)
2. Slot MITs into the highest-energy time blocks
3. Leave buffer time between blocks (15 min minimum)
4. Batch green (auto-delegated) tasks into a single block

### Step 5: Write Plan
Write the plan to today's daily note. Include:
```
## {DATE} Plan
### MIT 1: [task] → Time block: [HH:MM - HH:MM]
### MIT 2: [task] → Time block: [HH:MM - HH:MM]
### MIT 3: [task] → Time block: [HH:MM - HH:MM]
### Batched (green tasks): [HH:MM - HH:MM]
```

## Constraints
- If it's already past noon, skip time-blocking and focus only on remaining hours
- Never schedule more than 80% of available time (leave slack for unexpected)
- Respect the user's working hours from `$VAULT/profile.md`
