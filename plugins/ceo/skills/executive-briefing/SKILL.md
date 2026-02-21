---
name: executive-briefing
description: Multi-agent executive summary for board meetings, investor calls, quarterly reviews, or any moment requiring a synthesized view across all business domains. Delegates to all available agents and produces a formatted briefing document with audience-appropriate language.
---

# Executive Briefing Skill

You are producing an executive briefing. Your goal is to synthesize multi-domain business data into a narrative document that gives decision-makers a complete, accurate picture of the current situation — with the decisions they need to make clearly surfaced.

## When to Trigger

Trigger this skill when the user says:
- "Brief me on [topic/company/project]"
- "Prepare me for a board meeting"
- "I have an investor call — give me a briefing"
- "Quarterly review — what do I need to know?"
- "Give me an executive summary of everything"

## 4-Step Framework

### STEP 1: Scope Definition

Before gathering data, clarify:

1. **Audience**: Who is this briefing for?
   - Internal team: Operational detail, honest about problems
   - Board of directors: Strategic decisions, governance, risk
   - Investors: Growth narrative, metrics, milestones, use of funds
   - Media/PR: Controlled messaging, achievements, vision
   - All-hands: Motivating, transparent, future-focused

2. **Depth**: How much detail is needed?
   - 5-minute overview (key metrics only)
   - 20-minute deep dive (all domains, decisions required)
   - Full board pack (domain deep-dives, appendix with data)

3. **Domains to cover**: Which areas are relevant to this audience?
   - All domains (default for board/investor)
   - Financial + Product only (investor pitch focus)
   - Technical + Product only (team briefing)

4. **Time period**: What is the time scope?
   - Current snapshot (today)
   - Weekly / Monthly / Quarterly / Annual review
   - Since last milestone

If not stated, default to: All domains, quarterly scope, board audience, 20-minute depth.

---

### STEP 2: Agent Data Collection

Delegate to all available agents simultaneously. Request current-state snapshots:

**To `financial-advisor`** (if available):
- What are the current key financial metrics? (revenue, costs, burn rate, runway, MRR/ARR if applicable)
- What financial milestones were hit this period?
- What is the financial outlook for next period?
- What financial decisions are pending?

**To `product-manager`** (if available):
- What product milestones were shipped this period?
- What is the current user/customer growth trend?
- What are the top competitive developments?
- What are the most critical pending product decisions?

**To `tax-advisor`** (if available):
- What tax/compliance obligations are due this period?
- Are there any material compliance risks or recent changes?
- What regulatory developments are relevant to the business?

**To `ai-specialist`** (if available):
- What is the current technical health? (tech debt, test coverage, performance)
- What technical milestones were reached this period?
- What technical decisions are pending (architecture, tooling, team)?

Collect all outputs before proceeding to Step 3.

---

### STEP 3: Narrative Construction

Construct the executive narrative in this sequence:

1. **Situation** — Where are we today? (2-3 sentences per domain, synthesized)
2. **Key Findings** — What are the 3-5 most important things the audience needs to know?
3. **Decisions Required** — What decisions does the audience need to make? (Be specific)
4. **Recommendations** — What does the CEO recommend for each decision?
5. **Risks** — What are the top 3 risks to monitor?
6. **Wins** — What went well? (Essential for morale and credibility)

**Tone adjustment by audience**:
- **Board**: Formal, governance-focused, flag every material risk, quantify everything
- **Investors**: Growth-oriented, metrics-heavy, honest but optimistic, lead with traction
- **Team**: Transparent, honest about challenges, motivating, operational detail
- **Media**: Polished, achievement-focused, avoid internal metrics, control the narrative

---

### STEP 4: Briefing Document Assembly

Assemble the final document with these sections in order. Adjust depth based on requested format.

---

## Output Format

```markdown
# Executive Briefing — [Company/Project Name]
**Period**: [Time period]
**Date**: [Current date]
**Audience**: [Board / Investors / Team / etc.]
**Prepared by**: CEO Agent (coordinating: [agents used])

---

## One-Page Executive Summary

[5-7 bullet points maximum. The audience should understand the full picture after reading only this section.]

- **Overall Status**: 🟢 Strong / 🟡 Stable / 🔴 At-Risk
- **[Metric 1]**: [Value] ([+/-X% vs last period])
- **[Metric 2]**: [Value]
- **Top Win**: [Achievement]
- **Top Risk**: [Risk]
- **Key Decision Needed**: [Decision]

---

## Financial Overview

**Key Metrics**:
| Metric | Current | Last Period | Trend |
|--------|---------|-------------|-------|
| Revenue/MRR | $[X] | $[X] | 📈/📉/➡️ |
| Burn Rate | $[X]/mo | $[X]/mo | |
| Runway | [X] months | | |
| [Other] | | | |

**Financial Highlights**:
- [Highlight 1]
- [Highlight 2]

**Financial Risks**:
- [Risk 1]

---

## Product & Market Overview

**Key Metrics**:
| Metric | Current | Last Period | Trend |
|--------|---------|-------------|-------|
| Users/Customers | [X] | [X] | |
| [Key product metric] | | | |

**Product Highlights**:
- [Shipped: Feature/milestone]
- [Upcoming: Next major milestone]

**Competitive Updates**:
- [Notable competitor move or market development]

---

## Tax & Compliance Overview

**Current Status**: 🟢 Compliant / 🟡 Action Required / 🔴 At-Risk

**Upcoming Obligations**:
| Obligation | Deadline | Amount/Action |
|------------|----------|---------------|
| [Filing/Payment] | [Date] | [Detail] |

**Compliance Notes**:
- [Key regulatory note]

---

## Technical Overview

**Technical Health**: 🟢/🟡/🔴

| Indicator | Status |
|-----------|--------|
| Test Coverage | [X%] |
| Critical Bugs | [X open] |
| Tech Debt | Low/Medium/High |
| Deployment Reliability | [uptime or cadence] |

**Technical Highlights**:
- [Achievement or milestone]

**Pending Technical Decisions**:
- [Decision that needs input]

---

## Decisions Required

| Decision | Context | CEO Recommendation | Timeline |
|----------|---------|--------------------|----------|
| [Decision 1] | [Brief context] | [Recommendation] | [By when] |
| [Decision 2] | | | |

---

## Top 3 Risks to Watch

| Risk | Domain | Severity | Mitigation |
|------|--------|----------|------------|
| [Risk 1] | [Domain] | 🔴/🟡/🟢 | [Action] |
| [Risk 2] | | | |
| [Risk 3] | | | |

---

## Wins This Period

1. [Win 1]
2. [Win 2]
3. [Win 3]

---

## Next Period Priorities

1. [Priority 1] — Owner: [Role] — Target: [Date]
2. [Priority 2] — Owner: [Role] — Target: [Date]
3. [Priority 3] — Owner: [Role] — Target: [Date]

---

## Appendix: Agent Detail

### Financial Advisor Output
[Condensed version of financial-advisor findings]

### Product Manager Output
[Condensed version of product-manager findings]

### Tax Advisor Output
[Condensed version of tax-advisor findings]

### AI Specialist Output
[Condensed version of ai-specialist findings]

---

## Missing Agent Capabilities

[List unavailable agents and what data gaps exist as a result.]
```

---

## Quality Standards

1. The one-page executive summary must stand alone — the audience can stop after reading it
2. Every metric must have a trend indicator (up/down/flat)
3. Every risk must have a mitigation action — not just "monitor"
4. Decisions required must be specific — not "consider options" but "decide whether to hire a CTO by March 15"
5. Tone must match the stated audience — do not use internal jargon in investor briefings

---

**Reminder**: A briefing is not a data dump. Edit ruthlessly. The most important job is deciding what to leave out.
