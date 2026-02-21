# Weekly CEO Briefing Command

Delivers a structured weekly executive summary across all available domains — week summary, key metrics, decisions made, decisions pending, next week priorities, and risks to watch.

## Purpose

Get a weekly structured overview when:
- Starting Monday and want a clear picture of the week ahead
- Ending Friday and want to document the week's outcomes
- Preparing a weekly update for the team, board, or investors
- Wanting a consistent weekly rhythm of CEO-level situational awareness

## When to Use

**Use weekly-ceo-briefing when**:
- Running a weekly CEO review ritual
- Preparing a written update for stakeholders
- Wanting a structured end-of-week or start-of-week summary
- Replacing ad-hoc status checks with a consistent format

**Use `executive-briefing` skill when**:
- Preparing for a board meeting or investor call (formal, longer format)
- Need audience-specific language (board tone, investor tone)
- Need deep-dive appendix sections for each domain

## Command Format

```bash
/ceo:weekly-ceo-briefing [optional: week-ending-date]
```

### Optional Parameters

```
[week-ending-date]    ISO date or natural language for the week being reviewed
                      Examples: "2026-02-21", "this week", "last week"
                      Default: current week
```

## Examples

### Example 1: Current Week Briefing

```bash
/ceo:weekly-ceo-briefing
```

**Expected Output**:

```
# Weekly CEO Briefing
Week ending: February 21, 2026
Prepared by: CEO Agent | Agents: financial-advisor, product-manager, tax-advisor, ai-specialist

---

## 📊 Week Summary

**Overall Status**: 🟡 Stable — 2 items need attention

Strong product week with v1.3 shipped. Financial position holding with new trial
signups. One technical incident (resolved). Tax deadline approaching next month.

---

## Key Metrics

| Metric | This Week | Last Week | Trend |
|--------|-----------|-----------|-------|
| MRR | $44,200 | $42,000 | 📈 +5.2% |
| Active Users | 1,240 | 1,180 | 📈 +5.1% |
| New Trials | 38 | 29 | 📈 +31% |
| Trial → Paid | 12% | 11% | 📈 |
| Burn Rate | $28,000/mo | $28,000/mo | ➡️ |
| Runway | 7.8 months | 8.0 months | 📉 |
| Critical Bugs | 1 open | 3 open | 📈 (improving) |

---

## ✅ Decisions Made This Week

1. **Hired a part-time DevOps contractor** — Owner: CTO — to address deployment reliability
2. **Delayed feature X to Q2** — Owner: Product — to focus engineering on bug backlog
3. **Selected AWS eu-west-1 as primary EU data region** — Owner: Tech — for GDPR compliance

---

## ⏳ Decisions Pending

| Decision | Context | Deadline | Owner |
|----------|---------|----------|-------|
| Pricing tier change | Pro tier underpriced vs. competitors | March 1 | CEO |
| Fundraise vs. extend runway | 7.8 months runway | March 15 | CEO/CFO |
| Enterprise tier launch | 3 enterprise leads waiting | March 8 | Product/Sales |

---

## 🎯 Next Week Priorities

1. **Close 2 enterprise deals** — Owner: CEO — These are in final negotiation
2. **Ship payment bug fix to production** — Owner: Engineering — Blocking 12% of free-to-paid conversion
3. **Spanish tax filing preparation** — Owner: Finance/Tax — Deadline is March 15
4. **Kick off pricing audit** — Owner: Product/Finance — Input needed for March 1 decision

---

## ⚠️ Risks to Watch

| Risk | Domain | Level | Watch For |
|------|--------|-------|-----------|
| Runway under 8 months | Financial | 🔴 | New revenue or bridge needed by end of month |
| Enterprise deals stalling | Product/Sales | 🟡 | No response from [Company A] in 5 days |
| Q1 VAT filing — Spain | Tax | 🟡 | Deadline March 31 — start preparation week of March 1 |
| Competitor beta launch | Product | 🟡 | [Competitor] announced beta — monitor feature announcements |

---

## 🏆 Wins This Week

1. v1.3 shipped on time with 0 post-launch critical issues
2. 31% spike in trial signups — likely from [Blog Post / Mention]
3. Technical incident resolved in 47 minutes (below 1-hour SLA target)

---

## 📅 Coming Up

| Date | Event | Prep Needed |
|------|-------|-------------|
| Feb 24 | Enterprise demo — [Company A] | CEO + Product 30-min prep |
| Feb 28 | End of month metrics review | Gather MRR data, update dashboard |
| Mar 1 | Pricing decision deadline | Complete pricing audit |
| Mar 15 | Spain VAT Q4 filing | Start documentation this week |

---

💡 No missing agents. Full orchestration active.
```

### Example 2: Specific Week

```bash
/ceo:weekly-ceo-briefing 2026-02-14
```

Generates the briefing for the week ending February 14, 2026 using available historical data from repository and agents.

### Example 3: Minimal Agents

```bash
/ceo:weekly-ceo-briefing
```

*(When only financial-advisor is installed)*

**Expected Output**:

```
# Weekly CEO Briefing (Partial)
Week ending: [Date]
Agents: financial-advisor only

## ⚠️ Limited Briefing

Only financial domain available. Full briefing requires all agents.

## Financial Summary

[Financial metrics from financial-advisor]

## Missing This Week

- Product metrics — install product-manager for user/feature tracking
- Tax/compliance update — install tax-advisor for deadline tracking
- Technical health — install ai-specialist for code quality signals

💡 Install missing agents:
/plugin install product-manager@jontoio-claude-agents
/plugin install tax-advisor@jontoio-claude-agents
/plugin install ai-specialist@jontoio-claude-agents
```

## Output Format

Every weekly briefing includes:

1. **Week Summary** — 2-3 sentence overall characterization with status
2. **Key Metrics** — Per-domain metrics with week-over-week trend
3. **Decisions Made** — Explicit log of decisions taken this week
4. **Decisions Pending** — Upcoming decisions with deadline and owner
5. **Next Week Priorities** — Top 3-5 with owner and specific outcome
6. **Risks to Watch** — Risks to monitor, not just active crises
7. **Wins** — At least 3 positive things from the week
8. **Coming Up** — Key dates and events with prep requirements

## Tips for Consistent Weekly Use

1. **Run at the same time each week** — Friday afternoon or Monday morning both work; pick one
2. **Maintain a METRICS.md** — The CEO agent reads this file to track week-over-week trends
3. **Log decisions as you make them** — The briefing is more accurate when decisions are documented
4. **Note wins actively** — Teams under-document wins; the briefing surfaces them

## Integration

- **Monday use**: Orient for the week ahead — focus on priorities and upcoming deadlines
- **Friday use**: Capture the week's outcomes — focus on decisions made and wins
- **Stakeholder sharing**: Copy the briefing into your team update or investor email
- **Preceding board meeting**: Run `executive-briefing` skill after the weekly for a deeper board-ready document
