# Quick Capture

## Purpose
Instantly capture a thought, idea, task, or note to the inbox without breaking flow. The item will be triaged later.

## Workflow

### Step 1: Parse Input
The capture text is the remaining arguments after the subcommand.
Example: `/personal-secretary capture 下周三之前要提交项目方案给客户`
If no arguments provided, use AskUserQuestion to prompt: "What do you want to capture?"

### Step 2: Generate Title
Extract a short title (max 40 chars) from the capture text. Use the first meaningful phrase.

### Step 3: Create Inbox Item
Create a file at `$VAULT/0-Inbox/YYYY-MM-DD-HHMM - {title}.md` using the inbox-item template:
```markdown
---
captured: "{{DATETIME}}"
source: "Claude Code quick capture"
status: untriaged
---

# {{TITLE}}

{{CONTENT}}
```

### Step 4: Pre-classification (Optional)
If the content clearly sounds like a task, project, CRM entry, or decision, offer to pre-classify:
"这看起来像一个{任务/项目/联系人记录/决策}，要我直接帮你创建到对应的目录吗？"

If the user says yes, skip the inbox and create directly in the appropriate directory.

### Step 5: Confirm
Brief confirmation: "已捕获到 inbox: {{TITLE}}"

## Constraints
- This must be fast — one interaction maximum, ideally zero
- Don't over-analyze the content; triage happens later
- The goal is to reduce friction between thought and capture
