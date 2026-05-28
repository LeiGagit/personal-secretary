# Personal CRM

## Subcommands
Parse second argument: `add`, `list`, `view`, `update`, `log`, `followups`.

## Operation: add
1. Ask for contact name (required)
2. Ask for relationship type: Family, Friend, Colleague, Client, Mentor, Acquaintance, Other
3. Ask for contact frequency: Daily, Weekly, Biweekly, Monthly, Quarterly, Annually, As-needed
4. Ask for contact details (optional): phone, email, WeChat
5. Ask for important dates (optional): birthday, anniversaries
6. Set `last_contact` to today, calculate `next_contact_due` from frequency
7. Create file at `$VAULT/4-CRM/{name}.md` using the contact template
8. Confirm: "已创建联系人: {name}, 建议联系频率: {frequency}"

## Operation: list
1. Glob `$VAULT/4-CRM/*.md`
2. Display table sorted by `next_contact_due` (closest first):
```
## 联系人
| 姓名 | 关系 | 上次联系 | 下次应联系 | 频率 |
|------|------|----------|-----------|------|
```
3. Highlight contacts past due: highlight the row if `next_contact_due` < today

## Operation: view
1. Find contact file by name (fuzzy match)
2. Display full contact profile including interaction log

## Operation: update
1. Find contact file
2. Ask which field to update (use AskUserQuestion)
3. Update frontmatter or content
4. Confirm change

## Operation: log
1. Find contact file by name (fuzzy match)
2. Ask: "这次互动的内容是什么？"
3. Append to the Interaction Log table: date, context (meeting/call/message/other), notes
4. Update `last_contact` to today
5. Ask if `next_contact_due` should be recalculated based on frequency

## Operation: followups
1. Glob all contacts
2. Filter for `next_contact_due` <= today + 3 days (overdue or upcoming)
3. Sort by urgency (overdue first, then closest due date)
4. Present as:
```
📞 跟进提醒:

🔴 已逾期:
   • {name} - 上次联系 {date}, 应 {frequency} 联系一次

🟡 即将到期:
   • {name} - 下次联系应在 {date}

需要记录一次互动? 告诉我是哪位联系人。
```

## Constraints
- CRM is for personal relationships, not sales pipeline — keep it warm, not transactional
- Never suggest automated messages; the user writes their own
- The goal is remembering to nurture relationships, not gamifying them
