# 4-Color Task Priority System

## Overview
Every task is assigned one of four priority colors. This system combines the Eisenhower Matrix (urgent/important) with delegation awareness to prevent overload and ensure the right things get attention.

## Color Definitions

### Red — Personal Attention Required
**Meaning**: High priority, requires your unique skills or judgment. Cannot be delegated. Time-sensitive or high-stakes.

**Rules**:
- Maximum 5 active red tasks at any time
- These should be your MITs (Most Important Tasks)
- Red tasks that stay red for more than 2 weeks need re-evaluation

**Typical red tasks**:
- Strategic decisions
- Creative work requiring your voice
- High-stakes negotiations
- Crisis resolution

### Yellow — Needs Review/Feedback
**Meaning**: 80% complete, but someone else's input is needed to finish. Blocked on review, approval, or feedback.

**Rules**:
- Must have a `blocker` field identifying who/what is needed
- Should have a target resolution date
- If blocked for >1 week, escalate (nudge the reviewer)

**Typical yellow tasks**:
- Draft waiting for approval
- Work waiting for client feedback
- Deliverable needing peer review

### Green — Auto-Delegated / Routine
**Meaning**: Routine tasks with low cognitive load. Can be batched, automated, or delegated. Does not require deep thinking.

**Rules**:
- Batch similar green tasks together
- Review only during weekly review (not daily)
- If a green task keeps getting postponed, reconsider whether it needs to be done at all

**Typical green tasks**:
- Routine admin (expense reports, timesheets)
- Standard email replies
- Regular status updates
- Data entry, file organization

### Black — Deferred
**Meaning**: Not urgent and not important right now. Either consciously postponed or blocked with no near-term resolution.

**Rules**:
- Review all black tasks during weekly review
- If a task stays black for >2 weeks: either schedule it, reclassify it, or archive it
- Don't let black tasks accumulate — they create mental clutter

**Typical black tasks**:
- "Nice to have" improvements
- Ideas waiting for the right timing
- Tasks blocked on external factors with no ETA
- Low-priority research/exploration

## Decision Tree
When assigning a color, ask in this order:

1. **Is this urgent AND important?** → Red
2. **Is someone else's input needed to complete this?** → Yellow
3. **Is this routine / could someone else do it?** → Green
4. **Neither urgent nor important, or blocked long-term?** → Black

## Weekly Review Check
During weekly review, assess color distribution:
- Too many reds (>5): You're a bottleneck. What can be delegated?
- Too many yellows: You have a follow-up problem. Block on specific people.
- No greens: Everything feels like it needs personal attention. Find the 20% that can be batched.
- Too many blacks (>10): Clean house. Archive or delete the ones that no longer matter.

## Stored Format
```yaml
priority: red  # one of: red, yellow, green, black
```
