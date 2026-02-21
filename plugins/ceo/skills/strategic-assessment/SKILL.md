---
name: strategic-assessment
description: Full company or project situational analysis. Use when the user needs comprehensive understanding of their business position, wants a SWOT analysis, or asks "where do we stand?". Coordinates all available marketplace agents to produce a multi-domain situation report.
---

# Strategic Assessment Skill

You are performing a full strategic assessment. Your goal is to produce a CEO-level situational picture that synthesizes financial health, product-market fit, tax/compliance posture, and technical readiness into a single coherent view with prioritized action items.

## When to Trigger

Trigger this skill when the user says:
- "Assess our company / project"
- "Where do we stand?"
- "Give me a situational analysis"
- "Run a SWOT on us"
- "What's our strategic position?"

## 5-Step Framework

### STEP 1: Context Gathering

Before delegating to agents, gather baseline context:

1. **Scan the repository** for business signals:
   - Read `README.md`, `CLAUDE.md`, `package.json`, `pyproject.toml` (business model, tech stack)
   - Look for `CHANGELOG.md` or `ROADMAP.md` (product maturity signals)
   - Check `.env.example`, `docker-compose.yml` for third-party integrations (revenue/cost signals)
   - Read any `docs/` or `wiki/` files for product description

2. **Ask clarifying questions** if repo data is insufficient:
   - "What stage is the company/project? (idea, MVP, early revenue, scaling)"
   - "What is your primary revenue model? (subscription, usage-based, one-time, open source)"
   - "How many users/customers do you currently have?"
   - "What is your team size and composition?"
   - "What is your current monthly revenue and burn rate (if applicable)?"

3. **Identify which agents are available** for delegation (check sibling agent files).

---

### STEP 2: Agent Delegation

Send targeted sub-questions to each available agent. Delegate in parallel.

**To `financial-advisor`** (if available):
- What are the current and projected monthly costs (infrastructure, APIs, team)?
- What is the estimated monthly burn rate and runway?
- What is the revenue model and break-even point?
- What are the top 3 financial risks?

**To `product-manager`** (if available):
- What is the current product-market fit signal?
- Who are the primary competitors and how do we differentiate?
- What are the most critical product gaps for the next quarter?
- What is the user persona and their top unmet need?

**To `tax-advisor`** (if available):
- What is the current tax/compliance posture?
- Are there any immediate regulatory risks or filing obligations?
- What jurisdiction setup is in place and is it optimal?

**To `ai-specialist`** (if available):
- What is the current technical debt level?
- Are there significant AI/prompt optimization opportunities?
- What is the test coverage and code quality signal?
- What are the top 3 technical risks?

---

### STEP 3: Cross-Domain Synthesis

After collecting all agent outputs, identify:

**Conflicts**: Where agents disagree or surface competing priorities
- Example: "Product wants to build feature X; Finance says runway only supports feature Y"
- Example: "Tax-advisor flags jurisdiction risk that Product roadmap ignores"

**Alignments**: Where multiple agents agree, amplifying signal strength
- Example: "Both Finance and Product identify SMB market as highest-value segment"

**Dependencies**: Where one domain's decision gates another
- Example: "Tech debt must be resolved before Product can ship the API integration the Financial model depends on"

Explicitly call out all conflicts, alignments, and dependencies before building the SWOT.

---

### STEP 4: SWOT Construction

Build the SWOT from synthesized agent data. Every item must cite its source domain.

```
## SWOT Analysis

### Strengths (internal, positive)
- [S1] [Finding] — Source: [Agent/Domain]
- [S2] ...

### Weaknesses (internal, negative)
- [W1] [Finding] — Source: [Agent/Domain]
- [W2] ...

### Opportunities (external, positive)
- [O1] [Finding] — Source: [Agent/Domain]
- [O2] ...

### Threats (external, negative)
- [T1] [Finding] — Source: [Agent/Domain]
- [T2] ...
```

---

### STEP 5: Executive Recommendations

Produce a prioritized action list. Each action must have:
- **Priority**: P1 (this week) / P2 (this month) / P3 (this quarter)
- **Action**: Specific, verb-first description
- **Owner**: Which role or agent domain should lead
- **Success Metric**: How to know it's done
- **Timeline**: Target completion date or duration

Limit to top 5-7 actions to avoid overwhelm.

---

## Output Format

```markdown
# Strategic Assessment — [Company/Project Name]
**Date**: [Current date]
**Prepared by**: CEO Agent (coordinating: [list of agents used])

---

## Executive Summary

[3-5 sentences. Lead with the single most important finding. State overall strategic position — strong / stable / at-risk / critical. Name the top opportunity and the top threat.]

---

## Domain Findings

| Domain      | Status | Key Finding | Top Risk |
|-------------|--------|-------------|----------|
| Financial   | 🟢/🟡/🔴 | [1 line] | [1 line] |
| Product     | 🟢/🟡/🔴 | [1 line] | [1 line] |
| Tax/Legal   | 🟢/🟡/🔴 | [1 line] | [1 line] |
| Technical   | 🟢/🟡/🔴 | [1 line] | [1 line] |

---

## SWOT Analysis

[Full SWOT from Step 4]

---

## Cross-Domain Conflicts & Dependencies

[List any conflicts or dependencies identified in Step 3. If none, state "No material conflicts detected."]

---

## Prioritized Actions

| Priority | Action | Owner | Success Metric | Timeline |
|----------|--------|-------|----------------|----------|
| P1 | [Action] | [Owner] | [Metric] | [Date] |
| ... | | | | |

---

## Missing Agent Capabilities

[If any agents were unavailable, list what analysis was missing and suggest installation.]
```

---

## Quality Standards

A good strategic assessment:
1. Never gives generic advice — every point is grounded in data from the repo or agent outputs
2. Surfaces at least one cross-domain conflict or dependency
3. Provides a clear overall status (strong / stable / at-risk / critical)
4. Prioritizes actions — not everything can be P1
5. States confidence level for any domain where data was limited

---

**Reminder**: The CEO synthesizes — do not re-present each agent's full report. Extract the signal, resolve conflicts, and present one unified view.
