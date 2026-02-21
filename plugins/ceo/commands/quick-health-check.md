# Quick Health Check Command

Delivers a 2-3 minute company or project health snapshot across all available domains with traffic-light status, top risks, and one immediate action.

## Purpose

Get an instant, structured view of overall health when:
- Starting a new work session and need situational awareness
- Preparing for a meeting and need a fast status update
- Something feels off and you want to quickly diagnose which domain
- Checking in after a milestone or incident

## When to Use

**Use quick-health-check when**:
- Need a status overview in under 3 minutes
- Want traffic-light status per domain, not detailed analysis
- Checking overall health, not diagnosing a specific problem
- Preparing a quick verbal status update

**Use `strategic-assessment` skill when**:
- Need full SWOT analysis and prioritized action plan
- Preparing for board/investor meeting
- Making a major strategic decision

## Command Format

```bash
/ceo:quick-health-check [optional: focus-area]
```

### Optional Parameters

```
[focus-area]    Narrow the check to one domain or concern
                Examples: "financial", "product", "launch readiness", "technical"
```

## Examples

### Example 1: Full Health Check

```bash
/ceo:quick-health-check
```

**Expected Output**:

```
## Company Health Snapshot
Date: [Today]
Agents used: financial-advisor, product-manager, tax-advisor, ai-specialist

### Status Dashboard

| Domain    | Status | Key Signal                          |
|-----------|--------|-------------------------------------|
| Product   | 🟢     | v1.2 shipped, 3 open P1 issues      |
| Financial | 🟡     | $42k MRR, runway 8 months           |
| Tax/Legal | 🟢     | Q4 VAT filed, next deadline Mar 31  |
| Technical | 🟡     | 72% test coverage, 2 critical bugs  |

**Overall: 🟡 Stable — action required in 1 domain**

### Top 3 Risks
1. 🔴 Runway under 9 months without new revenue or fundraise — Financial
2. 🟡 2 critical bugs open in payment flow — Technical
3. 🟡 Competitive launch from [Competitor X] next month — Product

### Top 3 Opportunities
1. EU market expansion ready (tax setup complete) — Tax/Product
2. Token optimization audit could cut AI costs 20% — Technical/Financial
3. Enterprise tier launch would increase LTV 3x — Product/Financial

### Recommended Immediate Action
**Start fundraise process or close 5 enterprise deals** to extend runway beyond 12 months.
Owner: CEO/Founder | Timeline: This week

---
💡 Missing: No agents missing. Full orchestration active.
```

### Example 2: Focus Area Check

```bash
/ceo:quick-health-check financial
```

**Expected Output**:

```
## Financial Health Snapshot
Date: [Today]
Agent: financial-advisor

| Metric          | Value      | Status |
|-----------------|------------|--------|
| MRR             | $42,000    | 🟡     |
| Burn Rate       | $28,000/mo | 🟡     |
| Runway          | 8 months   | 🔴     |
| MoM Growth      | +8%        | 🟢     |
| Break-even MRR  | $55,000    | —      |

**Financial Status: 🔴 Runway critical**

Top financial risk: At current burn, out of cash by [Month+8].
Immediate action: Begin fundraise process or reduce burn by $8k/mo.
```

### Example 3: No Agents Installed

```bash
/ceo:quick-health-check
```

**Expected Output**:

```
⚠️ CEO Agent Alert: No marketplace agents detected.

Without companion agents, health check is limited to general strategic signals
from repository analysis.

## Repository Health Snapshot (Limited)

From README.md and project files:
- Product: [What can be inferred from docs]
- Technical: [What can be inferred from codebase]
- Financial: ❓ No financial-advisor agent — install for cost/revenue analysis
- Tax/Legal: ❓ No tax-advisor agent — install for compliance status

Install agents to unlock full health check:
/plugin install financial-advisor@jontoio-claude-agents
/plugin install product-manager@jontoio-claude-agents
/plugin install tax-advisor@jontoio-claude-agents
/plugin install ai-specialist@jontoio-claude-agents
```

## Output Format

Every health check includes:

1. **Status Dashboard** — Traffic-light per available domain with one-line key signal
2. **Overall Status** — Single 🟢/🟡/🔴 with brief characterization
3. **Top 3 Risks** — Highest severity risks across all domains
4. **Top 3 Opportunities** — Highest value opportunities spotted
5. **Recommended Immediate Action** — One specific action with owner and timeline

## Traffic Light Criteria

### 🟢 Healthy
- No critical blockers or risks
- Metrics trending in right direction
- No urgent action required

### 🟡 Attention Required
- At least one medium-priority risk
- Metrics flat or showing early warning signs
- Action needed within 1-2 weeks

### 🔴 Critical
- Active blocker or high-severity risk
- Metrics declining significantly
- Immediate action required

## Accuracy Notes

- Quick health checks have reduced depth vs. full skills
- Domain status is based on available signal — flag when data is insufficient
- Financial signals from repository alone have ±40% accuracy
- For decisions, use full skills not quick checks

## Integration with Other Commands

- **After seeing 🔴 on production**: Run `/ceo:production-go-nogo`
- **After seeing an opportunity**: Run `/ceo:opportunity-scan "[opportunity]"`
- **Before board/investor meeting**: Run `/ceo:weekly-ceo-briefing`
- **For full strategic review**: Use `strategic-assessment` skill
