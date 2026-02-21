---
name: opportunity-analysis
description: Business opportunity evaluation framework. Use when the user asks "should we build X?", "is market Y worth entering?", "should we pivot to Z?", or needs a structured evaluate-pursue-or-pass decision on a new idea, market, or product direction.
---

# Opportunity Analysis Skill

You are evaluating a business opportunity. Your goal is to produce a clear, evidence-backed verdict: **Pursue / Pursue with conditions / Deprioritize / Reject** — with the rationale and next steps if pursuing.

## When to Trigger

Trigger this skill when the user says:
- "Should we build X?"
- "Is market Y worth entering?"
- "Should we pivot to Z?"
- "Evaluate this idea / opportunity"
- "We're considering [new direction] — what do you think?"

## 5-Step Framework

### STEP 1: Opportunity Definition

Before delegating, clarify the opportunity precisely. Ask if not already stated:

1. **Market**: What specific market or customer segment is this targeting?
2. **Problem**: What specific problem does this solve? How is it currently solved?
3. **Solution**: What is our proposed solution? What is its core differentiator?
4. **Assumptions**: What must be true for this opportunity to be real? (List explicitly)
5. **Constraints**: What are our constraints? (Budget ceiling, timeline, team capacity, strategic fit)

Document the opportunity brief before proceeding:

```
Opportunity: [Name]
Market: [Who]
Problem: [What pain]
Solution: [Our approach]
Key assumptions: [List]
Constraints: [List]
```

---

### STEP 2: Market & Product Validation

Delegate to `product-manager` (if available):

- Who are the existing competitors in this space? How do they position?
- What is the evidence of demand? (search volume, waitlists, adjacent markets, customer interviews)
- What is the ideal customer persona for this opportunity?
- What product-market fit signals exist (or need to be tested)?
- How does this opportunity align or conflict with the existing product roadmap?
- What is the minimum viable product to test this opportunity?

If `product-manager` is unavailable:
- Ask the user to describe the competitive landscape and known demand signals
- Note confidence level is reduced without product agent

---

### STEP 3: Financial Modeling

Delegate to `financial-advisor` (if available):

- What is the Total Addressable Market (TAM), Serviceable Addressable Market (SAM), and Serviceable Obtainable Market (SOM) estimate?
- What are the unit economics? (CAC, LTV, payback period)
- What investment is required to test this opportunity? (MVP cost)
- What investment is required to fully pursue it? (full build cost)
- What is the projected ROI and timeline to profitability?
- How does this opportunity affect current burn rate and runway?

If `financial-advisor` is unavailable:
- Use rough estimates: TAM/SAM/SOM from market research, rough build cost estimate
- Note reduced confidence in financial projections

---

### STEP 4: Tax & Legal Scan

Delegate to `tax-advisor` (if available):

- Does entering this market create new tax obligations or jurisdiction exposure?
- Are there specific regulations governing this market? (GDPR, HIPAA, financial regulations, licensing requirements)
- Does this opportunity require a new legal entity or structure?
- Are there IP considerations (patents, trademarks, licensing)?

If `tax-advisor` is unavailable:
- Flag that regulatory and tax exposure have not been formally assessed
- Recommend a separate legal/tax review if opportunity is pursued

---

### STEP 5: CEO Verdict

Synthesize all domain inputs into a verdict. Apply this decision matrix:

**Scoring criteria** (each 0-10):
- Market attractiveness (size, growth rate, competitive intensity): 25%
- Strategic fit (alignment with core strengths, roadmap): 25%
- Financial viability (ROI, investment required, payback): 25%
- Execution feasibility (team capability, timeline, risk): 25%

**Verdict thresholds**:
- **Pursue** (≥7.5): High conviction — allocate resources, define milestones
- **Pursue with conditions** (5.0-7.4): Promising — validate specific assumptions first (state which ones)
- **Deprioritize** (3.0-4.9): Interesting but not now — revisit in [X] months when [condition] changes
- **Reject** (<3.0): Not worth pursuing — clear rationale required

**Auto-reject conditions** (state explicitly if any apply):
- Requires capabilities we demonstrably do not have and cannot acquire
- Regulatory barriers make entry infeasible without multi-year licensing process
- Unit economics are negative and no viable path to positive is identified
- Core assumptions have already been disproven by market evidence

---

## Output Format

```markdown
# Opportunity Analysis — [Opportunity Name]
**Date**: [Current date]
**Prepared by**: CEO Agent (coordinating: [agents used])

---

## Opportunity Brief

| Field | Detail |
|-------|--------|
| Market | [Who] |
| Problem | [Pain] |
| Solution | [Approach] |
| Key assumptions | [List] |
| Constraints | [List] |

---

## Domain Analysis

### Market & Product (from product-manager)
[Key findings: competitive landscape, demand signals, PMF evidence, MVP scope]

### Financial Model (from financial-advisor)
| Metric | Estimate | Confidence |
|--------|----------|------------|
| TAM | $[X]M | High/Med/Low |
| SAM | $[X]M | High/Med/Low |
| SOM (3yr) | $[X]M | High/Med/Low |
| MVP Cost | $[X]k | High/Med/Low |
| Full Build Cost | $[X]k | High/Med/Low |
| CAC | $[X] | High/Med/Low |
| LTV | $[X] | High/Med/Low |
| Payback Period | [X] months | High/Med/Low |

### Tax & Legal Scan (from tax-advisor)
[Key regulatory considerations, jurisdiction exposure, compliance requirements]

---

## Decision Scorecard

| Criterion | Weight | Score (0-10) | Weighted |
|-----------|--------|--------------|---------|
| Market attractiveness | 25% | X | X.X |
| Strategic fit | 25% | X | X.X |
| Financial viability | 25% | X | X.X |
| Execution feasibility | 25% | X | X.X |
| **Total** | **100%** | — | **X.X** |

---

## ✅ Verdict: [PURSUE / PURSUE WITH CONDITIONS / DEPRIORITIZE / REJECT]

[2-3 sentence rationale. Be specific. Reference the highest-signal data points.]

---

## Top 3 Reasons to Pursue *(if Pursue or Pursue with conditions)*

1. [Reason 1]
2. [Reason 2]
3. [Reason 3]

## Top 3 Risks

1. [Risk 1] — Mitigation: [action]
2. [Risk 2] — Mitigation: [action]
3. [Risk 3] — Mitigation: [action]

---

## Conditions to Validate *(if Pursue with conditions)*

Before committing resources, validate these assumptions:
1. [Assumption 1] — Validation method: [how] — Timeline: [X weeks]
2. [Assumption 2] — ...

---

## Next Steps *(if pursuing)*

| Step | Owner | Timeline | Success Metric |
|------|-------|----------|----------------|
| [Step 1] | [Role] | [Date] | [Metric] |
| [Step 2] | | | |

---

## Missing Agent Capabilities

[List unavailable agents and what analysis they would have added.]
```

---

## Quality Standards

1. The verdict must be one of the four options — no "it depends" without a lean
2. Assumptions must be explicitly listed, not buried in analysis
3. Financial estimates must state their confidence level
4. Rejected opportunities must have a clear, non-dismissive rationale
5. "Pursue with conditions" must specify exactly which conditions, not generic validation advice

---

**Reminder**: Opportunity cost is real — recommending "Pursue" means implicitly recommending deprioritizing something else. State what trade-off the user is making.
