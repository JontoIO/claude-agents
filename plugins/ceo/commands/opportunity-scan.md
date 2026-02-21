# Opportunity Scan Command

Delivers a rapid opportunity evaluation with a score, top reasons to pursue, top risks, and a clear recommended action (Explore / Pass / Pilot).

## Purpose

Get a fast opportunity assessment when:
- A new idea comes up in a meeting and you need a quick take
- A competitor move suggests a market gap worth evaluating
- Someone proposes a pivot and you need a structured first reaction
- You want to filter opportunities before investing in full analysis

## When to Use

**Use opportunity-scan when**:
- Need a verdict in 3-5 minutes
- Want a 1-10 score and top-line rationale
- Doing initial filtering of multiple ideas
- Need a "should we even look at this?" answer

**Use `opportunity-analysis` skill when**:
- Opportunity has passed initial filter and needs full evaluation
- Need TAM/SAM/SOM modeling
- Need full financial modeling and ROI timeline
- Making a resource commitment decision

## Command Format

```bash
/ceo:opportunity-scan "[opportunity description]"
```

The opportunity description should be a clear, specific statement of what you're evaluating. Vague descriptions yield less accurate scans.

## Examples

### Example 1: New Market Entry

```bash
/ceo:opportunity-scan "Launch a mobile app version of our web SaaS targeting field service workers"
```

**Expected Output**:

```
## Opportunity Scan — Mobile App for Field Service Workers
Date: [Today] | Scan type: Market expansion

### Opportunity Score: 7.2 / 10

**Recommendation: 🔍 EXPLORE**
*(Promising signal — do a 2-week discovery sprint before committing)*

---

### Top 3 Reasons to Pursue

1. **Underserved mobile segment**: Field service is mobile-first; our web-only product likely has <5% penetration in this segment despite market fit
2. **Pricing power**: Field service buyers typically pay 2-3x SaaS median per seat vs. desk workers — higher LTV per customer
3. **Competitive moat**: No dominant player in field service + [our core feature] combination identified

### Top 3 Risks

1. **Platform dependency**: iOS/Android app stores take 30% cut and control distribution — changes unit economics
2. **Scope creep**: Mobile UX requirements often drive significant backend refactoring — underestimated build cost
3. **Sales motion change**: Field service buyers often purchase through VARs/integrators — requires new distribution strategy

---

### Quick Financials Estimate

- Build cost (MVP): ~$80-120k (4-6 months, 2 engineers)
- Target market: ~500k field service SMBs in EU/US
- Comparable pricing: $49-99/user/month
- Conviction level: Medium (needs validation)

### Recommended Next Action: 🔍 EXPLORE

Run a 2-week discovery sprint:
1. Interview 10 field service managers about their current mobile tool stack
2. Audit competitors with mobile offerings (pricing, reviews, feature set)
3. Estimate backend changes required for offline-first architecture
Decide: Pilot or Pass after discovery.
```

### Example 2: Quick Pass

```bash
/ceo:opportunity-scan "Build a full HR module to compete with BambooHR"
```

**Expected Output**:

```
## Opportunity Scan — HR Module
Date: [Today]

### Opportunity Score: 2.8 / 10

**Recommendation: ⛔ PASS**

---

### Top 3 Reasons NOT to Pursue

1. **Entrenched competition**: HR SaaS is dominated by BambooHR, Rippling, Gusto, HiBob — all with $100M+ in funding and network effects in integrations
2. **Strategic misalignment**: HR is a completely separate domain from [current product] — zero capability leverage, doubles go-to-market complexity
3. **Build cost vs. outcome**: Competing HR suite requires 18-24 months minimum — same investment would likely return 5x more in core product depth

### Pass Rationale

No asymmetric advantage identified. Competing in a saturated market without differentiation or capability advantage is not a good use of resources at this stage.

If HR functionality is needed for customers, consider a **partnership or integration** with an existing HR vendor instead of building.
```

### Example 3: Pivot Evaluation

```bash
/ceo:opportunity-scan "Pivot from B2B SaaS to selling an API for developers"
```

**Expected Output**:

```
## Opportunity Scan — B2B SaaS → Developer API Pivot
Date: [Today]

### Opportunity Score: 6.1 / 10

**Recommendation: 🧪 PILOT**
*(Validate API demand without abandoning SaaS — run parallel for 60 days)*

---

### Top 3 Reasons to Pursue

1. **Lower sales friction**: API/developer model has self-serve viral loop; current SaaS likely requires sales-assisted conversion
2. **Market expansion**: Developer API opens adjacent segments (agencies, integrators) currently unreachable by direct SaaS sales
3. **Existing infrastructure**: If API is well-structured internally, external API requires mostly docs + auth layer, not full rebuild

### Top 3 Risks

1. **Revenue model disruption**: SaaS subscription → usage-based API has very different cash flow predictability and churn dynamics
2. **Customer success model changes**: Developers need different support (SDKs, documentation, sandbox) vs. SaaS users
3. **Monetization uncertainty**: Usage-based pricing is harder to forecast and budget for than subscriptions

### Recommended Next Action: 🧪 PILOT

Launch a private API beta to 10-20 developers (6-8 week pilot):
- Expose 2-3 core API endpoints
- Charge nominal usage fee to validate willingness to pay
- Measure: docs quality, integration time, support burden
Decide: Full API launch or continue SaaS-only after pilot data.
```

## Output Format

Every opportunity scan includes:

1. **Score** — Numeric 1-10 with confidence indication
2. **Recommendation** — One of: EXPLORE / PILOT / PASS
3. **Top 3 Reasons to Pursue** *(if EXPLORE or PILOT)*
4. **Top 3 Risks** — Always included
5. **Quick Financials Estimate** *(when sufficient signal)*
6. **Recommended Next Action** — Specific, time-boxed action

## Recommendation Definitions

| Recommendation | Meaning |
|----------------|---------|
| 🔍 EXPLORE | High signal — run a time-boxed discovery sprint (1-2 weeks) before deciding |
| 🧪 PILOT | Promising but uncertain — build a minimal test (4-8 weeks) to validate key assumptions |
| ⛔ PASS | Not worth pursuing — clear rationale given |

## Scoring Criteria (internal)

| Factor | Weight |
|--------|--------|
| Market attractiveness | 25% |
| Strategic fit | 25% |
| Estimated financial viability | 25% |
| Execution feasibility | 25% |

## Tips for Better Scans

1. **Be specific**: "Add AI features" → "Add AI-generated meeting summaries for sales calls"
2. **Include context**: "We already have X capability" helps assess strategic fit
3. **State constraints**: "We have 6 months runway" changes the calculus significantly
4. **Compare alternatives**: "vs. building feature Y instead" helps with opportunity cost

## Integration

- **After EXPLORE**: Run full `opportunity-analysis` skill for complete evaluation
- **After PILOT**: Review pilot results, then re-run opportunity scan with new data
- **After PASS**: Document why — useful when the same idea resurfaces later
