# Production Go/No-Go Command

Delivers a rapid launch readiness verdict with explicit blockers, conditions, and estimated time to production-ready.

## Purpose

Get a quick launch decision when:
- Sprint is ending and the team is debating whether to push to production
- A deadline is approaching and you need an honest assessment
- Stakeholders are asking "are we ready?"
- You want a sanity check before a planned launch date

## When to Use

**Use production-go-nogo when**:
- Need a launch verdict in under 5 minutes
- Want a top-line go/no-go with the 5 most critical blockers
- Preparing to talk to the team or stakeholders about launch timing
- Doing a quick pre-launch sanity check

**Use `production-readiness-analysis` skill when**:
- Need full traffic-light dashboard across all domains
- Want a complete 30-day launch checklist
- Need the full weighted scorecard methodology
- Preparing formal launch documentation

## Command Format

```bash
/ceo:production-go-nogo [product-name]
```

### Optional Parameters

```
[product-name]    Name or description of the product/feature being launched
                  Example: "payment module", "v2.0", "mobile app"
```

## Examples

### Example 1: Full Go/No-Go

```bash
/ceo:production-go-nogo "TaskFlow SaaS v1.0"
```

**Expected Output**:

```
## Production Go/No-Go — TaskFlow SaaS v1.0
Date: [Today] | Agents: financial-advisor, product-manager, tax-advisor, ai-specialist

### ❌ Verdict: NO-GO

Current score: 5.8/10 (threshold: 7.5 for GO)

---

### 🔴 Critical Blockers (must fix before launch)

1. **No error monitoring in place** (Technical) — Cannot detect production issues without Sentry/Datadog. Fix: 1-2 days
2. **Pricing page not live** (Product/Financial) — Users cannot convert. Fix: 3-5 days
3. **Privacy policy missing** (Tax/Legal) — GDPR violation risk from day 1. Fix: 2-3 days
4. **Payment flow has 2 critical bugs** (Technical) — Users cannot successfully pay. Fix: 3-7 days
5. **No customer support channel** (Product) — Cannot handle launch issues. Fix: 1 day

### 🟡 Conditions to Meet Within 30 Days of Launch

1. Implement rate limiting on API endpoints (Technical)
2. Set up automated backups with tested recovery procedure (Technical)
3. Register for VAT OSS if EU customers expected (Tax)

---

### Estimated Time to Production-Ready

**3-4 weeks** to resolve all critical blockers.

Suggested go-live date: [Current date + 4 weeks]

---

### Domain Status

| Domain    | Status | Blocker Count |
|-----------|--------|---------------|
| Product   | 🟡     | 1 critical    |
| Financial | 🟡     | 1 critical    |
| Tax/Legal | 🔴     | 1 critical    |
| Technical | 🔴     | 3 critical    |
```

### Example 2: Ready to Launch

```bash
/ceo:production-go-nogo "feature/user-export"
```

**Expected Output**:

```
## Production Go/No-Go — user-export feature
Date: [Today] | Agents: ai-specialist (only technical scope)

### ✅ Verdict: GO

Score: 8.2/10

No critical blockers detected.

### Conditions to Monitor Post-Launch

1. Watch for elevated export job queue depth (alert if >100 queued)
2. Verify S3 export file cleanup running after 24 hours

### Estimated Time to Production-Ready

Ready now. Recommend deploying during low-traffic window (weekday morning).
```

### Example 3: Partial Agents Available

```bash
/ceo:production-go-nogo "v1.0"
```

**Expected Output**:

```
## Production Go/No-Go — v1.0
Date: [Today] | Agents: financial-advisor (product-manager, tax-advisor, ai-specialist not installed)

### ⚠️ Verdict: PARTIAL GO/NO-GO (limited assessment)

Only financial domain assessed. Full go/no-go requires all agents.

### Financial Readiness: 🟡 Conditional

- Pricing defined: ✅
- Runway sufficient for launch costs: ✅
- Revenue model validated: ⚠️ Not tested with real customers

### Missing Assessment Areas

- Product readiness: Not assessed (install product-manager)
- Tax/Legal: Not assessed (install tax-advisor) — HIGH RISK if skipped
- Technical: Not assessed (install ai-specialist) — HIGH RISK if skipped

💡 Install missing agents before making a launch decision:
/plugin install product-manager@jontoio-claude-agents
/plugin install tax-advisor@jontoio-claude-agents
/plugin install ai-specialist@jontoio-claude-agents
```

## Output Format

Every production-go-nogo includes:

1. **Verdict** — Clear GO / GO WITH CONDITIONS / NO-GO
2. **Score** — Numeric score with threshold reference
3. **Critical Blockers** — Up to 5, with domain, description, and estimated fix time
4. **Conditions** — Items to address within 30 days if GO
5. **Domain Status** — Traffic-light per domain
6. **Estimated Time to Ready** — Concrete timeline or "Ready now"

## Verdict Criteria

| Verdict | Score | Description |
|---------|-------|-------------|
| ✅ GO | ≥7.5 | Launch recommended |
| ⚠️ GO WITH CONDITIONS | 6.0-7.4 | Launch possible; listed conditions must be met |
| ❌ NO-GO | <6.0 | Do not launch; resolve blockers first |

**Auto-veto**: Any domain scoring ≤3/10 triggers automatic NO-GO regardless of total score.

## Tips for Better Results

1. **Specify the product name**: Helps agents focus their assessment
2. **Mention known concerns**: "We have some open bugs" helps agents know where to look
3. **State the launch date**: "Launching Friday" changes the urgency of assessment
4. **Follow up with full skill**: For formal launches, run `production-readiness-analysis` for the complete checklist

## Integration

- **After NO-GO**: Assign blockers to team members, set re-check date
- **After GO**: Run `/ceo:weekly-ceo-briefing` to monitor post-launch metrics
- **Before board announcement**: Use `production-readiness-analysis` for formal documentation
