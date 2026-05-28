# Task Management

## Subcommands
Parse second argument for the operation. If no second argument, default to `list`.

| Operation | Description |
|-----------|-------------|
| `add <title>` | Create a new task |
| `list [filter]` | List tasks, optionally filtered by priority/status/project |
| `view <title>` | View full details of a specific task |
| `update <title>` | Update task fields |
| `complete <title>` | Mark task as completed |
| `delegate <title>` | Change task to green (auto-delegated) |
| `defer <title>` | Change task to black (deferred) |

## Operation: add
1. Take title from remaining arguments
2. Ask for priority using AskUserQuestion (options: Red/Personal, Yellow/Review, Green/Delegated, Black/Deferred)
3. If Red, check current count — warn if >= 5
4. If Yellow, ask what/who is the blocker
5. Ask for due date (optional) and estimated time (optional)
6. Create file at `$VAULT/2-Tasks/{title}.md` using the task template
7. Confirm: "已创建{颜色}任务: {title}"

## Operation: list
1. Glob `$VAULT/2-Tasks/*.md`
2. Filter by args if provided (e.g., `red`, `active`, `project-name`)
3. Sort by priority (red → yellow → green → black), then by due date
4. Display compact table:

```
## 当前任务

🔴 个人关注:
   [{status}] {title} {due_date} {project}

🟡 待审核:
   [{status}] {title} - 等待: {blocker}

🟢 可委托:
   [{status}] {title}

⚫ 已延后:
   [{status}] {title}
```

## Operation: view
1. Glob `$VAULT/2-Tasks/` for file matching the title (fuzzy match)
2. Read and display the full task content with all frontmatter fields

## Operation: update
1. Find the task file
2. Ask which field to update using AskUserQuestion
3. Update the frontmatter or content as requested
4. Append to the log section

## Operation: complete
1. Find the task file
2. Update status to `completed`, set `completed` date
3. Append to log: `- {DATE}: Completed`
4. Ask: "移到 99-Archive 还是保留在 Tasks 目录？"

## Operation: delegate / defer
1. Find the task file
2. Change priority to green (delegate) or black (defer)
3. Confirm the change

## Task Lifecycle
```
Captured (inbox) → Triaged → Active (colored) → Complete / Deferred
                                ↑                    ↓
                                └── Re-activated ←───┘
```
