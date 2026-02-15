# Monetization Planning Skill

A systematic framework for developing revenue strategies and pricing models for software projects.

## Overview

The Monetization Planning skill helps software teams design sustainable revenue models that align costs with income. It evaluates revenue strategies, designs pricing tiers, and projects revenue based on conversion rates and market dynamics.

## Purpose

- Design profitable revenue models for any project type
- Create pricing tiers that match costs and market expectations
- Project revenue based on realistic conversion assumptions
- Optimize pricing for customer value and business sustainability
- Ensure costs are covered with healthy margins

## When to Use

- Planning monetization before product launch
- Evaluating pricing strategy for existing products
- Exploring pivot from free to paid model
- Designing enterprise pricing tiers
- Planning open source sustainability (sponsorship, licensing)
- After cost estimation to ensure profitability
- When current pricing isn't covering costs
- Before fundraising (investors want revenue model)

## Revenue Models Covered

### 1. Freemium
Combination of free tier with limited features and paid upgrades.

**Best for**:
- SaaS applications
- API services
- Developer tools
- Products with viral potential

**Key Success Factors**:
- Free tier valuable enough to attract users
- Clear upgrade path (obvious value in paid)
- 2-5% free-to-paid conversion rate typical
- Free tier costs manageable

**Examples**:
- Slack: Free for small teams, paid for advanced features
- GitHub: Free public repos, paid for private and teams
- Vercel: Free for hobby projects, paid for production

### 2. Subscription (Tiered)
Multiple pricing tiers with increasing features and capabilities.

**Best for**:
- B2B SaaS
- Content platforms
- Professional tools
- Services with ongoing value

**Key Success Factors**:
- Clear differentiation between tiers
- Most customers choose middle tier (anchor pricing)
- Annual plans reduce churn (offer 2-month discount)
- Predictable recurring revenue

**Examples**:
- Netflix: Basic, Standard, Premium (resolution/screens)
- Notion: Free, Plus, Business, Enterprise
- Mailchimp: Free, Essentials, Standard, Premium

### 3. Usage-Based Pricing
Pay for what you use - scales with customer value.

**Best for**:
- APIs (per request)
- Infrastructure (compute/storage)
- AI services (per token/image/video)
- Variable usage patterns

**Key Success Factors**:
- Direct alignment: customer value = usage
- Predictable unit economics
- Free tier or generous trial to reduce friction
- Clear usage monitoring for customers

**Examples**:
- AWS: Pay per hour of compute, GB of storage
- Stripe: 2.9% + $0.30 per transaction
- Claude API: Pay per million tokens

### 4. Open Source Sponsorship
Community support through donations and sponsorships.

**Best for**:
- Open source libraries
- Developer tools
- Community-driven projects
- Projects with strong brand/following

**Key Success Factors**:
- Clear value proposition (why sponsor?)
- Recognize sponsors prominently
- Offer sponsor perks (logo placement, support priority)
- Multiple sponsorship tiers ($5, $25, $100, $1000/month)

**Examples**:
- Vue.js: Patreon + GitHub Sponsors (~$200k/year)
- webpack: OpenCollective ($400k/year)
- Babel: GitHub Sponsors + corporate sponsors

### 5. Enterprise Licensing
Custom contracts for large organizations with specific needs.

**Best for**:
- B2B software
- Tools requiring compliance (SOC2, HIPAA)
- On-premise deployments
- High-touch sales

**Key Success Factors**:
- Pricing based on seats, usage, or revenue
- Custom terms (SLAs, support, training)
- Annual contracts (predictable revenue)
- Typically 5-10x SaaS tier pricing

**Examples**:
- Slack: Enterprise Grid (custom pricing, $1k-10k+/month)
- GitHub: Enterprise Server (on-premise, custom pricing)
- Snowflake: Enterprise edition with custom contracts

### 6. Hybrid Model
Combination of multiple revenue streams.

**Best for**:
- Maximizing revenue across segments
- Open source with commercial offerings
- Multi-sided platforms

**Common Combinations**:
- Open source core + paid hosting (WordPress.com, GitLab)
- Freemium + enterprise licensing (Slack, Figma)
- Free consumers + paid business (Zoom, Dropbox)
- Usage-based + subscriptions (Twilio, Stripe)

**Examples**:
- GitLab: Free open source + paid tiers + enterprise
- MongoDB: Free open source + Atlas hosting + Enterprise
- Elastic: Open source + managed cloud + enterprise

## Framework: 5-Step Process

### Step 1: Project Classification
Identify project type, target audience, and value proposition.

**Questions to answer**:
- What type of software is this? (SaaS, API, open source, mobile, etc.)
- Who are the target customers? (Developers, businesses, consumers)
- What problem does it solve?
- What is the core value delivered?
- How is value measured? (Time saved, money earned, risk reduced)

### Step 2: Revenue Model Analysis
Evaluate applicable revenue strategies and their fit.

**Evaluation criteria**:
- Market expectations (what do competitors charge?)
- Value metric (what scales with customer value?)
- Sales complexity (self-serve vs high-touch?)
- Customer segment (SMB vs enterprise)
- Cost structure (fixed vs variable costs)

### Step 3: Pricing Strategy
Design specific pricing tiers and price points.

**Pricing considerations**:
- Cost-plus margin: Costs + desired margin (40-80% for SaaS)
- Value-based pricing: Fraction of value delivered (typically 10-20%)
- Competitive pricing: Market rates for similar products
- Psychological pricing: $99 vs $100, ending in 9 or 0
- Anchor pricing: High-priced tier makes middle tier look reasonable

### Step 4: Revenue Projections
Estimate revenue based on conversion rates and growth.

**Key metrics**:
- Free-to-paid conversion: 2-5% typical
- Free trial conversion: 15-25% typical (with credit card), 5-10% (without)
- Tier distribution: 60% lowest, 30% middle, 10% highest
- Annual vs monthly: 30-50% choose annual (with 15-20% discount)
- Churn rate: 5-7% monthly (consumer), 3-5% monthly (SMB), 1-2% annual (enterprise)

### Step 5: Recommendation
Propose best-fit monetization with implementation roadmap.

**Recommendation includes**:
- Primary revenue model
- Pricing tiers with specific prices
- Free tier strategy (if applicable)
- Revenue projections (12-24 months)
- Implementation timeline
- Key success metrics to track

## Pricing Tier Design

### Good Tier Structure

**Characteristics**:
- 3-4 tiers maximum (Free/Basic/Pro/Enterprise)
- Clear value differentiation at each tier
- Middle tier priced for target customer (anchor)
- Highest tier significantly more expensive (makes middle look good)
- Free tier valuable but limited (drives conversion)

**Example: SaaS Application**

```
Free (Lead Generation)
- 10 projects
- 1 user
- 7-day history
- Community support
Price: $0
Target: Hobbyists, trial users
Conversion goal: 5% to Starter

Starter (Individual professionals)
- Unlimited projects
- 1 user
- 90-day history
- Email support
- 100 AI requests/month
Price: $29/month ($24/month annual)
Target: Freelancers, small businesses
Margin: 70%+ (covers costs + profit)

Pro (Small teams) ⭐ POPULAR
- Everything in Starter
- 5 users ($10/additional user)
- Unlimited history
- Priority support
- 500 AI requests/month
- Advanced analytics
Price: $99/month ($79/month annual)
Target: Growing teams, SMBs
Margin: 75%
Expected: 60% of paid customers

Enterprise (Large organizations)
- Everything in Pro
- Unlimited users
- Custom AI request limits
- SLA (99.9% uptime)
- Phone support
- SSO, SAML
- Custom training
Price: Starting at $999/month (custom)
Target: Fortune 500, regulated industries
Margin: 80%+
Expected: 10% of paid customers (but 50% of revenue)
```

### Common Pricing Mistakes

**Mistake 1: Free tier too generous**
```
❌ Bad: Unlimited everything, just missing one feature
✅ Good: Clearly limited (10 projects, 1 user, 7-day history)
```

**Mistake 2: Unclear differentiation**
```
❌ Bad: Basic ($10) and Pro ($20) feel similar
✅ Good: Obvious value jump (10 → unlimited projects, +team features)
```

**Mistake 3: No enterprise tier**
```
❌ Bad: Top tier is $99/month (leaving money on table)
✅ Good: "Enterprise - Contact Sales" (capture high willingness to pay)
```

**Mistake 4: Pricing too low**
```
❌ Bad: $5/month (seems cheap, hard to cover costs)
✅ Good: $29-99/month (demonstrates value, covers CAC)
```

**Mistake 5: Too many tiers**
```
❌ Bad: 6 tiers (analysis paralysis)
✅ Good: 3-4 tiers (clear choice)
```

## Revenue Projection Model

### Formula

```
Monthly Recurring Revenue (MRR) =
  (Free Tier Users × Conversion Rate × Avg Price per Paid User) - Churn

Annual Recurring Revenue (ARR) = MRR × 12 × (1 - Average Annual Churn)

Lifetime Value (LTV) = Avg Revenue per User / Monthly Churn Rate

Example:
- 10,000 free users
- 5% conversion to paid
- Average paid user: $60/month
- 5% monthly churn

MRR = 10,000 × 0.05 × $60 = $30,000
ARR = $30,000 × 12 × (1 - 0.60) = $144,000
LTV = $60 / 0.05 = $1,200
```

### Tier Distribution

```
Typical distribution of paid users:
- Lowest tier: 60%
- Middle tier: 30%
- Highest tier: 10%

But revenue distribution inverted:
- Lowest tier: 20% of revenue
- Middle tier: 30% of revenue
- Highest tier: 50% of revenue

Example (1,000 paid users):
- Starter ($29): 600 users = $17,400/month (42%)
- Pro ($99): 300 users = $29,700/month (48%)
- Enterprise ($999): 100 users = $99,900/month (68%)

Wait, that's >100%?
Actually Enterprise is often custom: let's say avg $600
- Starter: 600 × $29 = $17,400 (37%)
- Pro: 300 × $99 = $29,700 (44%)
- Enterprise: 100 × $600 = $60,000 (73%)
Total: $107,100/month

So Enterprise (10% of users) = 56% of revenue
```

## Break-Even Analysis

### Formula

```
Break-even users = Monthly Costs / (Avg Revenue per User - Variable Cost per User)

Example:
- Monthly costs: $50,000
- Avg revenue per paid user: $80/month
- Variable cost per user: $5/month (API, hosting)
- Contribution margin: $80 - $5 = $75

Break-even: $50,000 / $75 = 667 paid users

With 5% free-to-paid conversion:
Need 667 / 0.05 = 13,340 total users to break even
```

### Margin Analysis

```
Gross Margin = (Revenue - Variable Costs) / Revenue

Healthy SaaS margins:
- 70-80%: Excellent (typical for mature SaaS)
- 60-70%: Good (growing SaaS)
- 40-60%: Concerning (high infrastructure or API costs)
- <40%: Unsustainable (need to optimize costs or raise prices)

Example:
Revenue: $100,000/month
Variable costs: $20,000/month (APIs, hosting, payment processing)
Gross margin: 80%

This leaves $80k for:
- Development team: $50k
- Sales & marketing: $20k
- Operations: $5k
- Profit: $5k
```

## Market Positioning

### Pricing Psychology

**Price Anchoring**:
```
Tier 1: $29/month
Tier 2: $99/month ⭐ POPULAR
Tier 3: $299/month

The $299 tier makes $99 look reasonable (even if few buy it)
Result: More customers choose $99 instead of $29
```

**Charm Pricing**:
```
$99/month feels significantly cheaper than $100/month
$997 feels cheaper than $1,000
But: $100 might feel more "premium" for enterprise products
```

**Annual Discount**:
```
Monthly: $99/month = $1,188/year
Annual: $948/year ($79/month) = 20% discount

Benefits:
- Improves cash flow (get 12 months upfront)
- Reduces churn (committed for year)
- Lower transaction fees (1 vs 12 payments)

Typically offer: 15-20% discount for annual
```

### Competitive Positioning

```
Market positioning:
- Premium: 2-3x market average (better features, support, brand)
- Market rate: Similar to competitors
- Value: 30-50% below market (volume strategy)

Example: Project management SaaS
- Asana Pro: $10.99/user/month
- Monday.com Standard: $8/user/month
- Trello Premium: $5/user/month
- You: $7/user/month (undercut Asana, above Trello)
```

## Open Source Monetization

### Sponsorship Model

**Tier Structure**:
```
Individual Supporters
- $5/month: Name in README
- $25/month: Name + logo in docs
- $100/month: Name + logo + monthly video call

Corporate Sponsors
- $500/month: Silver - Logo on website, priority issues
- $2,000/month: Gold - Above + priority features, listed as sponsor
- $5,000/month: Platinum - Above + custom development hours

Target: 1% of users as sponsors
Example: 10,000 users → 100 sponsors
- 70 @ $5 = $350
- 20 @ $25 = $500
- 8 @ $100 = $800
- 1 @ $500 = $500
- 1 @ $2,000 = $2,000
Total: $4,150/month ($50k/year)
```

### Dual Licensing

```
Open Source License: GPL, AGPL (copyleft)
+ Requires sharing modifications
+ Free for open source projects

Commercial License: Proprietary
+ No sharing requirement
+ Paid (one-time or annual)
+ Typical price: $500-5,000/year per developer

Example:
- MongoDB: SSPL (open) + Commercial
- Qt: GPL + Commercial
- MySQL: GPL + Commercial
```

### Hosted Service Model

```
Strategy: Free self-hosted + paid managed hosting

Example: GitLab
- GitLab CE: Free open source (self-host)
- GitLab.com: Free tier + paid plans ($19-99/user/month)
- GitLab Enterprise: Self-hosted premium ($19.95+/user/month)

Revenue split:
- .com paid: 60% of revenue
- Enterprise self-hosted: 35% of revenue
- Support contracts: 5% of revenue
```

## Implementation Roadmap

### Phase 1: Research (Weeks 1-2)
- [ ] Analyze competitor pricing
- [ ] Survey target customers (willingness to pay)
- [ ] Calculate unit economics (costs per user)
- [ ] Define value metric (what scales with value?)

### Phase 2: Design (Weeks 3-4)
- [ ] Design tier structure (3-4 tiers)
- [ ] Set price points based on research
- [ ] Define feature allocation per tier
- [ ] Create pricing page copy

### Phase 3: Implementation (Weeks 5-8)
- [ ] Implement payment processing (Stripe, Paddle)
- [ ] Build subscription management (upgrades, downgrades)
- [ ] Add usage tracking and limits
- [ ] Test checkout flow

### Phase 4: Launch (Week 9)
- [ ] Launch pricing page
- [ ] Email existing users about tiers
- [ ] Monitor conversion rates
- [ ] A/B test pricing (with caution)

### Phase 5: Optimization (Ongoing)
- [ ] Track metrics (conversion, churn, expansion revenue)
- [ ] Survey churned users (why did they leave?)
- [ ] Experiment with pricing (raise prices 10-20% annually)
- [ ] Add features to encourage upgrades

## Key Metrics to Track

### Conversion Metrics
- Free-to-paid conversion rate (target: 2-5%)
- Free trial conversion rate (target: 15-25% with CC, 5-10% without)
- Tier distribution (expect 60/30/10 split)
- Annual vs monthly split (target: 30-50% annual)

### Revenue Metrics
- Monthly Recurring Revenue (MRR)
- Annual Recurring Revenue (ARR)
- Average Revenue Per User (ARPU)
- Customer Lifetime Value (LTV)

### Health Metrics
- Churn rate (target: <5% monthly for SMB, <2% annual for enterprise)
- LTV:CAC ratio (target: >3:1)
- Gross margin (target: >70%)
- Net Revenue Retention (target: >100% with expansion)

## Integration with Other Skills

- **cost-estimation**: Use to set prices that cover costs plus margin
- **financial-risk-assessment**: Ensure revenue model addresses identified risks
- **roi-analysis**: Project ROI for investors based on revenue model

## Examples

See detailed examples in the `examples/` directory:
- [SaaS Monetization](../../agents/financial-advisor/examples/saas-startup.md)
- [Open Source Sponsorship](../../agents/financial-advisor/examples/open-source-lib.md)

## Tips and Best Practices

1. **Price for value, not cost** - Customers don't care about your costs
2. **Start higher** - Easier to lower prices than raise them
3. **Experiment carefully** - Test pricing with new customers first
4. **Annual discounts** - Improve cash flow and reduce churn
5. **Make middle tier obvious** - Most customers will choose it
6. **Enterprise "Contact Sales"** - Capture willingness to pay
7. **Grandfather existing customers** - Don't alienate early supporters
8. **Review annually** - Increase prices 10-20% as you add value
9. **Track everything** - Can't optimize what you don't measure
10. **Listen to customers** - But remember, they'll always say it's "too expensive"

## Limitations

- Revenue projections are estimates (actual results vary)
- Conversion rates depend heavily on product quality and marketing
- Competitive landscape changes (affects pricing power)
- Customer willingness to pay varies by market and geography
- Doesn't account for sales cycle length (B2B can be 3-12 months)

## Version History

- **1.0.0** (January 2025): Initial release with 5-step framework

## Related Resources

- [Financial Advisor Agent](../../agents/financial-advisor/README.md)
- [Monetization Strategy Review Command](../../commands/monetization-strategy-review.md)
- [Cost Estimation Skill](../cost-estimation/README.md)
