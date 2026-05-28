# Decision Records

## Subcommands
Parse second argument: `log`, `list`, `view`, `review`.

## Operation: log
1. Ask for the decision title
2. Guide through the decision template fields:
   - **Context**: What situation led to this decision? Why now?
   - **Options**: List at least 2 options with pros, cons, and risk level (Low/Medium/High)
   - **Decision**: What was chosen?
   - **Rationale**: Why this option over the others?
   - **Expected Outcomes**: What should happen as a result?
   - **Review Date**: When should this decision be revisited? (suggest 1-3 months out)
3. Create file at `$VAULT/5-Decisions/YYYY-MM-DD - {title}.md`
4. If a review_date is set, suggest adding it to the task system as a future review task

## Operation: list
1. Glob `$VAULT/5-Decisions/*.md`
2. Display compact table:
```
## 决策记录
| 日期 | 决策 | 状态 | 复盘日期 |
|------|------|------|---------|
```
3. Highlight decisions past their review date

## Operation: view
1. Find decision file by title (fuzzy match)
2. Display full decision record

## Operation: review
1. Find decisions with `review_date` <= today
2. If multiple, list them and ask which to review
3. For the selected decision, display the original record
4. Ask the review questions:
   - Actual outcome vs expected: What actually happened?
   - Would I make the same decision again knowing what I know now?
   - What did I learn from this decision?
5. Append the review answers to the decision file
6. Ask if a follow-up review date is needed (if the outcome is still unfolding)

## Constraints
- Decisions don't need to be big — any choice with trade-offs is worth recording
- The value is in the review: learning from past decisions is the point
- Don't over-engineer small decisions ("what to eat for lunch" is not a decision record)
- A good litmus test: "Will I benefit from reviewing this decision in 3 months?"
