# Periodic Reviews

## Subcommands
Parse second argument: `weekly`, `monthly`, `quarterly`.

## Weekly Review

### Workflow
1. Create review file at `$VAULT/6-Reviews/Weekly/YYYY-W{week}.md` from template
2. **Clear inbox**: Process all untriaged items in `$VAULT/0-Inbox/`. Triage or schedule triage.
3. **Review tasks**: List all active tasks by color. For each:
   - Red: Still relevant? Still red? If >5, force-rank.
   - Yellow: Any unblocked? Follow up on blockers >1 week.
   - Green: Any that can be batched and done now?
   - Black: Any that should be archived (>2 weeks stale)?
4. **Review goals**: Check quarterly goal progress. Are weekly actions aligned?
5. **Habit check**: Review this week's habit completion. Any patterns?
6. **Calendar preview**: Check next week for time-sensitive items.
7. **Set next week's focus**: 1-3 themes or goals.
8. **Reflection questions**:
   - What worked well this week?
   - What needs improvement?
   - What's the #1 thing to accomplish next week?

### Output
Write the completed review to the review file with all sections filled.

## Monthly Review

### Workflow
1. Create review file at `$VAULT/6-Reviews/Monthly/YYYY-MM.md` from template
2. **Goal check**: Review monthly goals vs actual outcomes
3. **Task analytics**: Count tasks created/completed/carried-forward by color
4. **Habit trends**: Calculate completion rates and streaks for each habit
5. **Energy audit**: Ask the user to reflect on high/low energy patterns
6. **Financial check-in**: Quick income/expense overview (if user tracks this)
7. **Key learnings**: What did this month teach you?
8. **Next month focus**: Set the theme and priorities

## Quarterly Review

### Workflow
1. Create review file at `$VAULT/6-Reviews/Quarterly/YYYY-Q{N}.md` from template
2. **Goal achievement**: Each quarterly goal — % complete, actual vs target
3. **Key wins**: Top 3 accomplishments this quarter
4. **Key challenges**: What got in the way?
5. **Stop/Start/Continue**: What to stop doing, start doing, continue doing
6. **Annual goal alignment**: Are quarterly results on track for annual goals?
7. **Life balance check**: Rate each life area 1-10 (Career, Health, Relationships, Wealth, Growth, Spirit)
8. **Next quarter planning**: Set theme, goals, and key results for next quarter

## Constraints
- Weekly review: thorough but efficient, ~15 min
- Monthly review: deeper reflection, ~30 min
- Quarterly review: strategic, may take 45-60 min — encourage the user to find quiet time
- All reviews should reference the user's vision and annual goals for alignment
