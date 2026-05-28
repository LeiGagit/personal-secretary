# Morning Briefing

## Workflow

### Step 1: Determine Date
Use today's date in YYYY-MM-DD format. Check if a daily note exists at `$VAULT/1-Daily/YYYY-MM-DD.md`. If not, create it from the template at `$VAULT/9-Templates/daily-note.md`.

### Step 2: Collect Information
1. **Yesterday's carryover**: Read yesterday's daily note (if exists), extract incomplete MITs and tasks
2. **Active tasks**: Glob `$VAULT/2-Tasks/*.md`, filter for status=active, sort by priority (red → yellow → green → black)
3. **Follow-ups due today**: Glob `$VAULT/4-CRM/*.md`, check `next_contact_due` field for today's date
4. **Calendar**: Check for any calendar references in today's daily note or upcoming items in `$VAULT/6-Reviews/`
5. **Weather**: If `$VAULT/profile.md` has a `location` field, offer to fetch weather via WebFetch. Otherwise skip.

### Step 3: Generate Briefing
Present a concise morning briefing:

```
🌅 早上好，{{NAME}}！今天是 {{DATE}} {{DAY_OF_WEEK}}

## 📋 今日待办 (按优先级)
🔴 个人关注:
   [list red tasks, max 5]
🟡 待审核:
   [list yellow tasks]
🟢 可批处理:
   [list green tasks]

## 🔄 昨日未完成
   [carryover items]

## 📞 今日跟进提醒
   [follow-ups due today]

## 🎯 建议今日 3 个 MIT
   1. [suggested]
   2. [suggested]
   3. [suggested]
```

### Step 4: Confirm MITs
Use AskUserQuestion to let the user confirm or adjust the 3 MITs. Then write them to today's daily note in the Morning Briefing section.

### Step 5: Set Session Tasks
Use TaskCreate to add the 3 MITs as session tasks for tracking during the day.

## Constraints
- Keep the briefing concise — the user wants to start their day, not read a novel
- Only show items that need attention today; hide deferred/archived tasks
- If there are more than 5 red tasks, flag it: "⚠️ 你有超过 5 个红色任务，建议在 weekly review 中重新排序优先级"
