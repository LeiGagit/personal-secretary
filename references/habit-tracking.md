# Habit Tracking

## Subcommands
Parse second argument: `define`, `log`, `review`, `list`.

## Operation: define
1. Ask for habit name (e.g., "晨跑", "阅读 30 分钟", "冥想")
2. Ask for category: Health, Growth, Productivity, Relationships, Spirit, Other
3. Ask for frequency: Daily, Weekly, Weekdays, Custom
4. Ask for target count (e.g., 1 time per day, 3 times per week)
5. Ask for streak goal (e.g., 21 days, 66 days)
6. Ask: "做这个习惯的触发条件是什么？" (cue)
7. Ask: "完成后的奖励或感受是什么？" (reward)
8. Create file at `$VAULT/8-Habits/{name}.md` using the habit-definition template
9. Confirm: "已创建习惯: {name}"

## Operation: log
1. List all active habits
2. Ask: "记录今天的习惯完成情况吗？"
3. For each habit, ask: "完成了吗？" (Yes/No/Skip)
4. Create or update `$VAULT/8-Habits/YYYY-MM-DD.md` using the habit-log template
5. Update streak counters in the habit definition file:
   - If completed: streak++, check if new best streak
   - If not completed: streak resets to 0
6. Summarize: "今天 {completed}/{total} 项习惯完成"

## Operation: review
1. Ask for time period: week, month, or custom range
2. Glob habit log files in the date range
3. Calculate for each habit:
   - Completion rate (%)
   - Current streak
   - Best streak
   - Trend (improving/declining/stable)
4. Display table:
```
## 习惯回顾 ({period})

| 习惯 | 完成率 | 当前连续 | 最佳连续 | 趋势 |
|------|--------|---------|---------|------|
| 晨跑 | 85% | 12天 | 18天 | 📈 |
| 阅读 | 60% | 3天 | 8天 | 📉 |
```

5. Offer insights:
   - Which habits are sticking? Which are struggling?
   - Any patterns? (e.g., "周末完成率明显低于工作日")
   - Should any habits be adjusted? (easier target, different cue, etc.)

## Operation: list
1. Glob `$VAULT/8-Habits/*.md` (habit definitions, not logs)
2. Display table:
```
## 习惯列表
| 习惯 | 类别 | 频率 | 当前连续 | 最佳连续 |
|------|------|------|---------|---------|
```

## Constraints
- Habits are about consistency, not perfection — missing a day is information, not failure
- If a habit has <50% completion rate for >2 weeks, suggest reducing scope ("Maybe start with 5 minutes instead of 30?")
- The cue-reward pattern comes from Atomic Habits (James Clear) — honour it
- Don't overwhelm: suggest tracking max 5 habits at a time for new users
