# Inbox Triage

## Purpose
Process all untriaged inbox items and classify them into the appropriate locations.

## Workflow

### Step 1: List Inbox Items
Glob `$VAULT/0-Inbox/*.md`. Filter for status=untriaged.
Present a summary: "你有 X 个未处理的 inbox 条目"

### Step 2: Process Each Item
For each inbox item, read the content and present a brief summary (1-2 sentences).

Use AskUserQuestion to classify:
- **Task** → Create in `$VAULT/2-Tasks/` using the task template, ask for priority (red/yellow/green/black)
- **Project** → Create in `$VAULT/3-Projects/` using the project template
- **CRM Entry** → Create in `$VAULT/4-CRM/` using the contact template
- **Decision Record** → Create in `$VAULT/5-Decisions/` using the decision template
- **Reference** → Ask where to save (could be a note in the vault, or an external tool)
- **Someday/Maybe** → Append to `$VAULT/7-Planning/Someday.md` (create if missing)
- **Trash** → Delete the inbox item

### Step 3: Update or Delete Inbox Item
After classification:
- If moved to another directory: delete the inbox item
- If kept as reference: update status to "triaged"

### Step 4: Complete
Report: "Triage 完成。处理了 X 条: Y 个任务, Z 个项目, ..."

## Constraints
- Don't rush — this is a deliberate process. Each item deserves a decision.
- If the user is uncertain, default to "Someday/Maybe" rather than deleting
- For tasks, always ask about due date and priority
- For projects, ask about the desired outcome (Key Results)
