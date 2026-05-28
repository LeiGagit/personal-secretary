# Life Planning

## Subcommands
Parse second argument: `vision`, `goals`, `review`.

## Operation: vision

### View Vision
Read and display `$VAULT/7-Planning/Vision.md`. If it doesn't exist, offer to create it.

### Create/Edit Vision
1. Use the vision template from `$VAULT/9-Templates/vision.md`
2. Guide the user through each section with AskUserQuestion:
   - **Career & Contribution**: What impact do you want to make through your work? (5-10 year view)
   - **Relationships & Family**: What kind of relationships do you want to cultivate?
   - **Health & Vitality**: What does your ideal health look like?
   - **Wealth & Freedom**: What level of financial freedom do you seek?
   - **Learning & Growth**: Who do you want to become through learning?
3. **Core Values**: Ask for 5 core values. Probe: "When have you felt most fulfilled? What value was being honored?"
4. **5-Year Picture**: "If you woke up 5 years from now and everything had gone better than expected, what would your life look like?"
5. Write to `$VAULT/7-Planning/Vision.md`

## Operation: goals

### View Goals
If no year specified, show current year's annual goals and current quarter's goals.

### Create/Edit Annual Goals
1. Use the annual-goals template
2. For each life area (Career, Health, Relationships, Wealth, Growth), ask:
   - What's one goal for this year in this area?
   - What are 1-2 measurable key results?
3. Set quarterly checkpoints with review dates
4. Write to `$VAULT/7-Planning/Goals-{YEAR}.md`

### Create/Edit Quarterly Goals
1. Use the quarterly-goals template
2. Derive from annual goals — each quarterly goal should map to an annual goal
3. For each goal, define clear key results (measurable, time-bound)
4. Set monthly milestones
5. Write to `$VAULT/7-Planning/Goals-{YEAR}-Q{Quarter}.md`

## Operation: review
1. Read the vision, annual goals, and current quarterly goals
2. Present alignment check:
   - Are daily/weekly actions moving toward quarterly goals?
   - Are quarterly goals aligned with annual goals?
   - Is the vision still accurate? (vision should be reviewed annually or after major life changes)
3. Flag misalignments: "你本季度的目标是 X，但过去两周的任务主要集中在 Y。需要调整目标还是调整时间分配？"

## Constraints
- Vision work is personal — be supportive, not prescriptive
- Goals should be ambitious but believable. "What would 70% achievement look like?"
- Never judge the user's goals or values. The secretary's job is to help articulate and track, not evaluate.
