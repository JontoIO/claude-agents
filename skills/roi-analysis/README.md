# ROI Analysis Skill

A systematic framework for calculating Return on Investment (ROI) for software projects, features, and business decisions.

## Overview

The ROI Analysis skill provides structured methods to evaluate whether investments in software development, infrastructure, or business initiatives will generate sufficient returns. It helps make data-driven go/no-go decisions.

## Purpose

- Calculate financial return on investment for projects
- Determine break-even points and payback periods
- Compare multiple investment options objectively
- Model best-case, worst-case, and realistic scenarios
- Provide decision frameworks for stakeholders
- Justify budget allocations and resource commitments

## When to Use

- Evaluating whether to build a new feature
- Deciding between build vs buy options
- Assessing infrastructure investments
- Prioritizing projects by financial return
- Justifying budget requests to stakeholders
- Comparing architectural alternatives
- Making hiring decisions (will additional headcount pay off?)
- Vendor contract negotiations (multi-year vs annual)

## Core ROI Concepts

### Basic ROI Formula

```
ROI = (Net Profit / Investment Cost) × 100%

Where:
Net Profit = Total Return - Total Investment
```

**Example**:
```
Investment: $50,000 (feature development)
Return: $150,000 (revenue over 2 years)
Net Profit: $100,000
ROI: ($100,000 / $50,000) × 100% = 200%
```

### Payback Period

Time required to recover the initial investment.

```
Payback Period = Investment Cost / Average Monthly Return

Example:
Investment: $50,000
Monthly return: $5,000
Payback period: 10 months
```

### Break-Even Point

When cumulative returns equal cumulative costs.

```
Break-even point occurs when:
Cumulative Revenue = Cumulative Costs

Example:
Build feature: $50,000
Ongoing cost: $1,000/month
Revenue from feature: $6,000/month
Net monthly: $5,000
Break-even: 10 months
```

### Net Present Value (NPV)

Accounts for time value of money (a dollar today is worth more than a dollar tomorrow).

```
NPV = Σ (Cash Flow_t / (1 + r)^t) - Initial Investment

Where:
r = discount rate (typically 10-15% for software)
t = time period

Example:
Year 0: -$50,000 (investment)
Year 1: +$30,000 (return)
Year 2: +$35,000 (return)
Discount rate: 10%

NPV = -$50,000 + ($30,000/1.1) + ($35,000/1.1²)
    = -$50,000 + $27,273 + $28,926
    = $6,199

Positive NPV = Good investment
Negative NPV = Poor investment
```

### Customer Lifetime Value (LTV)

Total revenue expected from a customer over their lifetime.

```
LTV = (Average Revenue per User × Gross Margin%) / Churn Rate

Example:
ARPU: $100/month
Gross margin: 80%
Monthly churn: 5%

LTV = ($100 × 0.80) / 0.05 = $1,600

Rule of thumb: LTV should be >3x CAC
```

## Framework: 5-Step Process

### Step 1: Investment Calculation

Calculate all costs associated with the investment.

**One-time Costs**:
- Development time (hours × hourly rate)
- Design and planning
- Testing and QA
- Deployment and launch
- Training and documentation
- Legal or compliance costs

**Ongoing Costs**:
- Maintenance (typically 10-20% of dev cost annually)
- Infrastructure and hosting
- Third-party services
- Support and operations
- Opportunity cost (what else could team build?)

**Example: New Feature**
```
One-time:
- Development: 200 hours @ $100/hr = $20,000
- Design: 40 hours @ $85/hr = $3,400
- Testing: 40 hours @ $80/hr = $3,200
- Total one-time: $26,600

Ongoing (monthly):
- Maintenance: 8 hours/month @ $100/hr = $800
- Infrastructure: $50/month
- Third-party API: $100/month
- Total ongoing: $950/month ($11,400/year)

Total 2-year investment:
- One-time: $26,600
- Ongoing: $11,400 × 2 = $22,800
- Total: $49,400
```

### Step 2: Return Estimation

Estimate financial returns from the investment.

**Direct Revenue**:
- New customer acquisition
- Upsells to higher tiers
- Reduced churn (retained revenue)
- Price increases (enabled by new value)

**Cost Savings**:
- Reduced manual work (automation)
- Lower infrastructure costs (optimization)
- Fewer support tickets (better UX)
- Reduced technical debt (easier future development)

**Intangible Benefits** (try to quantify):
- Improved brand reputation
- Competitive advantage
- Team morale and retention
- Market positioning

**Example: New Feature (AI Summarization)**
```
Direct revenue:
- Enables Pro tier pricing ($99 vs $49)
- Expect 30% of users to upgrade for this feature
- Current: 200 users @ $49 = $9,800/month
- After: 200 users, 60 upgrade to $99
  * 140 @ $49 = $6,860
  * 60 @ $99 = $5,940
  * Total: $12,800/month
- Revenue increase: $3,000/month ($36,000/year)

Cost savings:
- Reduces support tickets by 20% (users self-serve)
- Current support cost: $2,000/month
- Savings: $400/month ($4,800/year)

Total return:
- Year 1: $36,000 + $4,800 = $40,800
- Year 2: $40,800 (assume flat)
- Total 2-year: $81,600
```

### Step 3: Timeframe Analysis

Calculate when investment pays off.

**Break-Even Point**:
```
Using example above:
Investment: $49,400
Monthly return: $3,400 ($3,000 revenue + $400 savings)

Break-even: $49,400 / $3,400 = 14.5 months
```

**Payback Period**:
```
More detailed (accounting for ongoing costs):
Monthly net: $3,400 return - $950 ongoing cost = $2,450 net
Payback: $26,600 one-time / $2,450 net = 10.9 months

After payback, monthly profit: $2,450
```

**Time Value Considerations**:
- Money returned sooner is more valuable
- 6-month payback is excellent
- 12-month payback is good
- 24-month payback is acceptable
- >24-month payback is risky (long bet)

### Step 4: Scenario Modeling

Model multiple scenarios to understand risk.

**Best Case** (80th percentile outcome):
```
Assumptions:
- Feature is huge hit
- 50% of users upgrade (vs 30% expected)
- Support tickets reduced 30% (vs 20% expected)

Revenue: $5,000/month (vs $3,000)
Savings: $600/month (vs $400)
Total return: $5,600/month

Break-even: 4.8 months
2-year ROI: 320%
```

**Realistic Case** (50th percentile outcome):
```
Assumptions:
- Original estimates hold
- 30% of users upgrade
- 20% support reduction

Revenue: $3,000/month
Savings: $400/month
Total return: $3,400/month

Break-even: 10.9 months
2-year ROI: 165%
```

**Worst Case** (20th percentile outcome):
```
Assumptions:
- Lower adoption than expected
- 15% of users upgrade (vs 30%)
- 10% support reduction (vs 20%)

Revenue: $1,500/month
Savings: $200/month
Total return: $1,700/month

Break-even: 15.6 months (but ongoing costs eat into it)
Net monthly: $1,700 - $950 = $750
Actually break-even: 35 months
2-year ROI: 36% (marginal)
```

**Probability Weighted**:
```
Best case (20% probability): 320% ROI
Realistic (60% probability): 165% ROI
Worst case (20% probability): 36% ROI

Expected ROI = (0.2 × 320%) + (0.6 × 165%) + (0.2 × 36%)
             = 64% + 99% + 7.2%
             = 170% (strong expected return)
```

### Step 5: Decision Framework

Provide clear go/no-go recommendation.

**Decision Criteria**:

**Strong Yes** (Build it):
- ROI >200% over 2 years
- Payback period <12 months
- Positive ROI in realistic AND worst-case scenarios
- Strategic importance (competitive advantage)

**Yes** (Build it):
- ROI 100-200% over 2 years
- Payback period 12-18 months
- Positive ROI in realistic scenario, breakeven in worst case
- Aligns with product strategy

**Maybe** (Needs more analysis or smaller scope):
- ROI 50-100% over 2 years
- Payback period 18-24 months
- Negative ROI in worst case
- Consider MVP or phased approach

**No** (Don't build):
- ROI <50% over 2 years
- Payback period >24 months
- Negative ROI in realistic scenario
- Better alternatives exist (higher ROI projects)

**Example Decision**:
```
AI Summarization Feature:
- Realistic ROI: 165%
- Payback: 10.9 months
- Worst-case ROI: 36% (still positive)
- Expected ROI: 170%

DECISION: YES, BUILD IT
- Strong ROI in realistic scenario
- Acceptable payback period
- Even worst case is positive (de-risks investment)
- Enables competitive positioning
```

## ROI Calculation Templates

### Template 1: New Feature ROI

```markdown
## Feature: [Name]

### Investment
**One-time**:
- Development: [X] hours @ $[Y]/hr = $[Z]
- Design: [X] hours @ $[Y]/hr = $[Z]
- Testing: [X] hours @ $[Y]/hr = $[Z]
- Total one-time: $[TOTAL]

**Ongoing** (monthly):
- Maintenance: $[X]
- Infrastructure: $[X]
- Third-party: $[X]
- Total monthly: $[TOTAL]

**Total 2-year**: $[ONE-TIME + (MONTHLY × 24)]

### Return
**Revenue Impact**:
- [Description of how it generates revenue]
- Estimated: $[X]/month

**Cost Savings**:
- [Description of cost reduction]
- Estimated: $[X]/month

**Total Return** (monthly): $[TOTAL]

### Analysis
- Break-even: [MONTHS]
- Payback period: [MONTHS]
- 2-year ROI: [PERCENTAGE]

### Scenarios
| Scenario | Adoption | Revenue | Savings | Break-even | ROI |
|----------|----------|---------|---------|------------|-----|
| Best     | [X]%     | $[Y]/mo | $[Z]/mo | [M] months | [R]% |
| Realistic| [X]%     | $[Y]/mo | $[Z]/mo | [M] months | [R]% |
| Worst    | [X]%     | $[Y]/mo | $[Z]/mo | [M] months | [R]% |

### Decision: [YES / NO / MAYBE]
**Rationale**: [1-2 sentences explaining decision]
```

### Template 2: Build vs Buy ROI

```markdown
## Decision: Build [Solution] vs Buy [Vendor]

### Option A: Build Custom

**Investment**:
- Development: $[X]
- Ongoing maintenance: $[Y]/month
- Total 3-year: $[Z]

**Benefits**:
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

**3-year TCO**: $[TOTAL]

### Option B: Buy [Vendor]

**Investment**:
- Integration: $[X] one-time
- Monthly subscription: $[Y]/month
- Total 3-year: $[Z]

**Benefits**:
- [Benefit 1]
- [Benefit 2]
- [Benefit 3]

**3-year TCO**: $[TOTAL]

### Comparison
| Factor | Build | Buy | Winner |
|--------|-------|-----|--------|
| Year 1 cost | $[X] | $[Y] | [Build/Buy] |
| Year 3 cost | $[X] | $[Y] | [Build/Buy] |
| Customization | High | Limited | Build |
| Time to market | [X] weeks | [Y] weeks | [Build/Buy] |
| Maintenance | Internal | Vendor | [Build/Buy] |
| Scalability | [Rating] | [Rating] | [Build/Buy] |

### Break-even Analysis
- If using for [X] years: [Build/Buy] is cheaper
- Break-even point: [Y] years

### Decision: [BUILD / BUY]
**Rationale**: [1-2 sentences]
```

### Template 3: Hiring ROI

```markdown
## Hiring Decision: [Role]

### Investment
**Year 1**:
- Salary: $[X]
- Benefits: $[Y] (typically 20-30% of salary)
- Recruiting: $[Z] (internal time + fees)
- Onboarding: $[W] (training, ramp-up)
- Total Year 1: $[TOTAL]

**Ongoing** (Year 2+):
- Compensation: $[SALARY + BENEFITS]
- Annual increase: ~5-7%

### Return
**Productivity**:
- Expected output: [X] feature hours/month
- Value of features: $[Y] (revenue or cost savings)

**Opportunity Cost**:
- Current: [What we can't build without this hire]
- With hire: [What becomes possible]

**Team Multiplier**:
- Frees up [X] hours/month from existing team
- Value: $[Y]/month

**Total Return** (monthly): $[TOTAL]

### Analysis
- Break-even: [MONTHS]
- Year 1 ROI: [PERCENTAGE]
- Year 2+ ROI: [PERCENTAGE]

### Decision: [HIRE / DON'T HIRE / DEFER]
**Rationale**: [Consider: Can we afford it? Do we have enough work? Will revenue support it?]
```

## Common ROI Use Cases

### Use Case 1: Performance Optimization

**Question**: Should we spend 2 weeks optimizing page load times?

**Investment**:
- 2 weeks × 2 developers = 160 hours @ $100/hr = $16,000

**Return**:
- Improved conversion rate: 2.5% → 3.0% (0.5% improvement)
- Current revenue: $50,000/month from 500 conversions
- New revenue: $60,000/month from 600 conversions
- Increase: $10,000/month

**ROI**:
- Payback: 1.6 months
- Year 1 ROI: 650%
- **Decision: YES, excellent ROI**

### Use Case 2: Technical Debt

**Question**: Refactor authentication system now or later?

**Option A: Refactor Now**
- Investment: $30,000 (300 hours)
- Benefit: Prevents $50,000 emergency refactor in 18 months
- Ongoing: Saves 10 hours/month maintenance = $1,000/month

**Option B: Defer**
- No immediate cost
- Risk: Emergency refactor in 18 months = $50,000
- Ongoing: Current high maintenance cost

**ROI**:
- If refactored now: Cost $30,000, save $50,000 + ($1,000 × 18) = $68,000
- Net benefit: $38,000
- **Decision: YES, refactor now**

### Use Case 3: Infrastructure Migration

**Question**: Migrate from VMs to containers?

**Investment**:
- Migration: 400 hours @ $90/hr = $36,000
- Testing: 80 hours @ $80/hr = $6,400
- Total: $42,400

**Return**:
- Infrastructure savings: $2,000/month (more efficient resource usage)
- Faster deployments: 5 hours/week saved = $2,000/month
- Total: $4,000/month

**ROI**:
- Payback: 10.6 months
- 2-year ROI: 225%
- **Decision: YES, strong ROI**

## Tips and Best Practices

1. **Be conservative with returns** - Better to under-promise and over-deliver
2. **Account for opportunity cost** - What else could team build?
3. **Include intangibles** - Brand value, competitive positioning, team morale
4. **Model scenarios** - Best/realistic/worst case reduces surprise
5. **Track actual vs projected** - Improve future ROI estimates
6. **Short payback periods are king** - <12 months is excellent in software
7. **Don't forget ongoing costs** - Maintenance compounds over time
8. **Consider strategic value** - Sometimes low-ROI projects are strategic necessities
9. **Probability-weight scenarios** - Expected value = better decision
10. **Review regularly** - ROI changes as project evolves

## Limitations

- ROI projections are estimates, not guarantees
- Hard to quantify intangible benefits (brand, morale)
- Doesn't account for risks or probability explicitly (use scenarios)
- Assumes linear returns (reality may differ)
- Opportunity cost is theoretical (team might not build alternative)
- External factors (market changes, competitors) can invalidate assumptions

## Integration with Other Skills

- **cost-estimation**: Provides investment cost inputs for ROI
- **monetization-planning**: Provides revenue projection inputs
- **financial-risk-assessment**: Identifies risks that could impact ROI

## Version History

- **1.0.0** (January 2025): Initial release with 5-step framework

## Related Resources

- [Financial Advisor Agent](../../agents/financial-advisor/README.md)
- [Cost Estimation Skill](../cost-estimation/README.md)
- [Monetization Planning Skill](../monetization-planning/README.md)
