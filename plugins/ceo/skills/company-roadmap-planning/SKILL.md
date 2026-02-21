---
name: company-roadmap-planning
description: Strategic roadmap creation across all business domains. Use when the user asks "create a roadmap for the next 6/12 months", "what should we focus on next?", or needs a cross-functional timeline integrating product, financial, compliance, and technical milestones.
---

# Company Roadmap Planning Skill

You are building a strategic company roadmap. Your goal is to produce a cross-functional timeline that integrates milestones from all domains into a single coherent plan — with dependencies made explicit and success metrics defined for each milestone.

## When to Trigger

Trigger this skill when the user says:
- "Create a roadmap for the next [6/12/18] months"
- "What should we focus on next?"
- "Help us plan the next quarter / year"
- "Build our strategic roadmap"
- "Align our roadmap across teams"

## 6-Step Framework

### STEP 1: Current State Audit

Delegate to all available agents for a current-state snapshot before planning forward.

**To `financial-advisor`** (if available):
- What is the current runway and burn rate?
- What are the current revenue and growth metrics?
- What financial milestones have been hit vs. missed?

**To `product-manager`** (if available):
- What features have shipped vs. what is still in backlog?
- What does the current product-market fit signal look like?
- What is the current user/customer count and growth rate?

**To `tax-advisor`** (if available):
- What are the upcoming mandatory compliance deadlines?
- Are there structural changes needed (entity, jurisdiction) that affect timing?

**To `ai-specialist`** (if available):
- What is the current technical debt burden?
- What infrastructure or architectural changes are needed before the next growth phase?

Summarize current state before proceeding. This is the baseline.

---

### STEP 2: Goal Setting

Work with the user to define the planning horizon and goals:

1. **Planning horizon**: 3 months / 6 months / 12 months / 18 months
2. **Primary objective**: What is the single most important outcome by end of period?
   - Examples: "Reach $10k MRR", "Launch in 3 EU markets", "Raise Series A", "Ship v2.0"
3. **Secondary objectives** (max 3): What other outcomes matter?
4. **Constraints**: What is fixed? (budget ceiling, team size, regulatory deadlines)
5. **OKR structure** (if user wants OKRs):
   - Objective: [Aspirational outcome]
   - Key Results: [3-5 measurable outcomes that indicate objective achievement]

If the user has not provided goals, ask:
- "What does success look like by [end of planning horizon]?"
- "What is the single most important thing to achieve?"
- "What constraints should the roadmap respect?"

---

### STEP 3: Product Roadmap Integration

Delegate to `product-manager` (if available):

- What features or product milestones should be on the roadmap for this period?
- How should features be prioritized? (RICE, value/effort, strategic alignment)
- What are the dependencies between features?
- What user research or validation is needed before building?
- What is the recommended sequencing?

Structure the output as a quarterly breakdown:
- Q[N]: [Feature/milestone 1], [Feature/milestone 2]
- Q[N+1]: [Feature/milestone 3], [Feature/milestone 4]

If `product-manager` unavailable, ask the user for their current feature backlog and help prioritize using RICE scoring.

---

### STEP 4: Financial Milestones

Delegate to `financial-advisor` (if available):

- What revenue targets should be set for each quarter?
- What are the funding milestones? (next raise, profitability date)
- What is the projected cost trajectory as the roadmap executes?
- What financial decisions are gated on roadmap milestones? (hire when MRR reaches $X)
- What is the burn rate at each phase of the roadmap?

Structure as quarterly financial targets:
- Q[N]: Revenue target, Burn rate, Key financial decision
- Q[N+1]: ...

If `financial-advisor` unavailable, ask the user for current financials and set rough targets.

---

### STEP 5: Compliance Timeline

Delegate to `tax-advisor` (if available):

- What are the mandatory regulatory deadlines in the planning period?
- Are there jurisdiction registrations or filings tied to expansion plans?
- What compliance work must be completed before specific product milestones?
- Are there tax filing dates that affect cash flow planning?

Build a compliance calendar to overlay on the roadmap:
- [Month]: [Filing/deadline/registration]

If `tax-advisor` unavailable, flag that compliance deadlines have not been formally assessed and recommend a separate review.

---

### STEP 6: Integrated Roadmap

Merge all domain inputs into a single cross-functional timeline. Map dependencies explicitly:

**Dependency notation**:
- `→` (enables): Milestone A must complete before Milestone B can start
- `↔` (parallel): Milestones can run simultaneously
- `⚡` (conflict): Milestones compete for the same resource

Identify the critical path — the sequence of dependent milestones that determines the earliest possible completion date for the primary objective.

---

## Output Format

```markdown
# Company Roadmap — [Company/Project Name]
**Planning Horizon**: [Duration]
**Date**: [Current date]
**Prepared by**: CEO Agent (coordinating: [agents used])

---

## Strategic Objectives

**Primary Objective**: [Single most important outcome]

**OKRs**:
| Objective | Key Result | Target | Owner |
|-----------|------------|--------|-------|
| [O1] | [KR1] | [Metric] | [Role] |
| | [KR2] | | |
| [O2] | [KR1] | | |

---

## Current State Baseline

| Domain | Current Status | Key Metric | Gap to Goal |
|--------|---------------|------------|-------------|
| Product | [Status] | [Metric] | [Gap] |
| Financial | [Status] | [Metric] | [Gap] |
| Tax/Legal | [Status] | [Metric] | [Gap] |
| Technical | [Status] | [Metric] | [Gap] |

---

## Integrated Roadmap

### Q[N] — [Quarter label, e.g. "Q1 2026: Foundation"]

**Theme**: [1 phrase describing the quarter's focus]

| Domain | Milestone | Owner | Dependencies | Success Metric |
|--------|-----------|-------|-------------|----------------|
| Product | [Milestone] | [Role] | [Dep or "None"] | [Metric] |
| Financial | [Milestone] | [Role] | [Dep or "None"] | [Metric] |
| Tax/Legal | [Milestone] | [Role] | [Dep or "None"] | [Metric] |
| Technical | [Milestone] | [Role] | [Dep or "None"] | [Metric] |

**Key dependency**: [Most critical dependency this quarter]

---

### Q[N+1] — [Quarter label]

[Repeat structure]

---

### Q[N+2] — [Quarter label] *(if 12-month horizon)*

[Repeat structure]

---

### Q[N+3] — [Quarter label] *(if 12-month horizon)*

[Repeat structure]

---

## Critical Path

The primary objective depends on this sequence:

```
[Milestone A] → [Milestone B] → [Milestone C] → [Primary Objective]
Timeline: [Q1] → [Q2] → [Q3] → [Q4]
Risk: [What could delay this path]
```

---

## Key Dependencies Map

| Milestone | Depends on | Enables | Earliest Start |
|-----------|------------|---------|----------------|
| [Milestone] | [Dep] | [Next milestone] | [Date] |

---

## Compliance Calendar

| Month | Obligation | Amount/Action | Responsible |
|-------|-----------|---------------|-------------|
| [Month] | [Filing/deadline] | [Detail] | [Role] |

---

## Resource Plan

| Quarter | Team Size | Key Hires Needed | Budget Required |
|---------|-----------|-----------------|----------------|
| Q[N] | [X] | [Role] | $[X] |
| Q[N+1] | | | |

---

## Milestones Summary

| Milestone | Quarter | Domain | Success Metric | Status |
|-----------|---------|--------|---------------|--------|
| [Milestone] | Q[N] | [Domain] | [Metric] | Planned |

---

## Review Cadence

- **Weekly**: Review this week's milestones vs. plan
- **Monthly**: Adjust roadmap based on new data (market, financial, technical)
- **Quarterly**: Full roadmap refresh — reassess goals, re-prioritize

---

## Missing Agent Capabilities

[List unavailable agents and what roadmap gaps exist as a result.]
```

---

## Quality Standards

1. Every milestone must have a measurable success metric — not "improve performance" but "reduce p95 latency to <200ms"
2. The critical path must be explicitly identified — not implied
3. Dependencies must be real — only list dependencies that actually block execution
4. The roadmap must be achievable within stated constraints (budget, team, time)
5. Quarters must have themes — single-word or short-phrase that unifies the quarter's intent

---

**Reminder**: A roadmap is a commitment to priorities, not a wish list. Every item on the roadmap means something else is not on it. Make that trade-off explicit.
