---
name: competitive-intelligence
description: Conduct comprehensive competitive analysis including competitor identification, feature comparison matrix, pricing research, SWOT analysis, and strategic positioning recommendations
---

# Competitive Intelligence Skill

Research competitors, analyze their features and positioning, identify market gaps, and provide strategic recommendations for differentiation and competitive advantage.

## When to Use This Skill

Use this skill when you need to:
- Understand the competitive landscape for a product
- Build a feature comparison matrix vs competitors
- Research competitor pricing models and strategies
- Identify white space opportunities in the market
- Develop strategic positioning recommendations
- Assess competitive threats and advantages
- Inform product roadmap with competitive insights

## 7-Step Competitive Intelligence Framework

### Step 1: Competitor Identification (10-15 min)

**Objective**: Identify direct, indirect, and emerging competitors

**Actions**:
1. **Repository Analysis**: Read README, docs, and package files to understand the product category
2. **Web Search - Direct Competitors**: Search for "[product category] alternatives", "[product type] competitors", "best [product category] tools"
3. **Web Search - Market Category**: Search for "[category] market landscape 2025", "[category] vendor comparison"
4. **Competitor Segmentation**:
   - **Direct competitors**: Same problem, same solution approach, same target audience
   - **Indirect competitors**: Same problem, different solution approach or audience
   - **Emerging competitors**: New entrants, VC-backed startups, open source alternatives
5. **Prioritize 5-7 Key Competitors**: Focus on most relevant based on market share, feature overlap, and target audience

**Output Format**:
```markdown
## Competitor Landscape

### Direct Competitors (3-4)
- **[Competitor Name]**: [Brief description, target audience, key strength]
  - Website: [URL]
  - Positioning: [How they describe themselves]
  - Notable: [Market share, funding, or distinguishing feature]

### Indirect Competitors (2-3)
- **[Competitor Name]**: [Why indirect, what overlap exists]

### Emerging Competitors (1-2)
- **[Competitor Name]**: [Why watching, potential threat]
```

---

### Step 2: Feature Matrix Construction (20-30 min)

**Objective**: Create comprehensive feature comparison matrix

**Actions**:
1. **Feature Inventory**: List all features from the product being analyzed (from README, docs, repo analysis)
2. **Competitor Feature Research**: For each competitor, web search for:
   - "[competitor name] features"
   - "[competitor name] pricing page" (often lists features by tier)
   - "[competitor name] documentation"
   - "[competitor name] vs [another competitor]" (comparison articles)
3. **Feature Categorization**: Group features into logical categories:
   - Core functionality (must-have features)
   - Advanced features (power user features)
   - Integration & ecosystem (API, webhooks, extensions)
   - Collaboration & sharing
   - Security & compliance
   - Analytics & reporting
   - Platform & deployment (cloud, self-hosted, mobile)
4. **Scoring System**: For each feature, use:
   - ✅ **Full support**: Feature is fully implemented
   - 🟡 **Partial support**: Feature exists but limited
   - ❌ **Not supported**: Feature missing
   - 🔜 **Announced/Beta**: On roadmap or in beta
   - ❓ **Unknown**: Could not verify

**Output Format**:
```markdown
## Feature Comparison Matrix

| Feature Category | Feature | [Product] | [Competitor 1] | [Competitor 2] | [Competitor 3] |
|------------------|---------|-----------|----------------|----------------|----------------|
| **Core Functionality** |
| [Feature 1] | | ✅ | ✅ | 🟡 | ❌ |
| [Feature 2] | | ✅ | ❌ | ✅ | ✅ |
| **Advanced Features** |
| [Feature 3] | | 🟡 | ✅ | ✅ | 🔜 |

### Feature Gaps
**Where competitors lead**:
- [Feature X]: Available in [Competitor 1, 2] but not in [Product]
- [Feature Y]: [Competitor 3] offers advanced version, we have basic

**Where we lead**:
- [Feature Z]: Unique to [Product], key differentiator
- [Feature W]: More advanced implementation than competitors
```

---

### Step 3: Value Proposition Analysis (15-20 min)

**Objective**: Extract and compare competitor positioning and messaging

**Actions**:
1. **Homepage Messaging**: For each competitor, visit homepage and extract:
   - Primary headline (the H1)
   - Subheadline (supporting copy)
   - Key benefits (usually 3-5 bullet points or sections)
   - Call-to-action (what they want users to do)
2. **Target Audience Signals**: Identify who they're targeting:
   - Language used (technical vs business, beginner vs advanced)
   - Social proof (customer logos, case studies)
   - Use cases highlighted
3. **Value Proposition Themes**: Categorize messaging:
   - Speed/performance ("10x faster", "real-time")
   - Ease of use ("no-code", "5-minute setup")
   - Cost ("free forever", "50% cheaper")
   - Features ("most comprehensive", "all-in-one")
   - Trust ("enterprise-grade", "SOC 2 compliant")
   - Innovation ("AI-powered", "next-generation")
4. **Messaging Gaps**: Identify underserved value props in the market

**Output Format**:
```markdown
## Value Proposition Analysis

| Competitor | Primary Message | Target Audience | Key Themes | Differentiation |
|------------|-----------------|-----------------|------------|-----------------|
| [Competitor 1] | "[H1 headline]" | [Audience] | Speed, Enterprise | AI-powered automation |
| [Competitor 2] | "[H1 headline]" | [Audience] | Ease, Cost | Free tier, no-code |

### Messaging Patterns
- **Most common themes**: [Speed, Ease of use, etc.]
- **Underserved themes**: [What no one is emphasizing]
- **Recommended positioning**: [Where whitespace exists]
```

---

### Step 4: Pricing Intelligence (15-20 min)

**Objective**: Understand competitive pricing models and strategies

**Actions**:
1. **Pricing Model Research**: For each competitor, web search for "[competitor name] pricing"
2. **Document Pricing Structure**:
   - Model type: Free tier, freemium, free trial, usage-based, per-seat, tiered
   - Tiers: Number of tiers, names, price points
   - Limits: User limits, usage limits, feature gating
   - Enterprise: Custom pricing, contracts
3. **Feature-to-Price Mapping**: Note which features are gated at which tier
4. **Value Metrics**: Identify pricing axes:
   - Per-seat, per-project, per-MAU, per-API-call
   - Storage, bandwidth, compute
   - Features, integrations, support level
5. **Pricing Psychology**: Note tactics:
   - Anchoring (expensive tier to make mid-tier look good)
   - "Most popular" badges
   - Annual discounts (15-20% common)
   - Free trials vs freemium

**Output Format**:
```markdown
## Pricing Comparison

| Competitor | Model | Free Tier | Entry Paid | Mid Tier | Enterprise |
|------------|-------|-----------|------------|----------|------------|
| [Competitor 1] | Freemium, per-seat | $0 (5 users) | $15/user | $30/user | Custom |
| [Competitor 2] | Free trial, usage | 14-day trial | $49/mo | $199/mo | Custom |

### Pricing Insights
- **Most common model**: [Freemium per-seat with 3 tiers]
- **Entry price range**: [$10-50/month or per-seat]
- **Value metrics**: [Users, projects, API calls]
- **Monetization strategy**: [Feature gating, usage limits, support tiers]
- **Recommendation**: [Suggested pricing strategy based on market positioning]
```

---

### Step 5: Strengths & Weaknesses Assessment (15-20 min)

**Objective**: SWOT analysis of each competitor and market position

**Actions**:
1. **Strengths Identification**: For each competitor, note:
   - Market position (leader, challenger, niche)
   - Unique features or capabilities
   - Customer base (size, notable customers)
   - Technical advantages (performance, scalability)
   - Business advantages (funding, team, partnerships)
2. **Weaknesses Discovery**: Web search for:
   - "[competitor name] reviews" (G2, Capterra, Trustpilot)
   - "[competitor name] complaints" or "issues"
   - Reddit, HackerNews, Twitter sentiment
   - GitHub issues (if open source)
   - Common complaints: pricing, UX, performance, support, missing features
3. **Opportunity Spotting**: Identify market gaps:
   - Features requested but not available
   - Underserved user segments
   - Emerging trends competitors are slow to adopt
   - Business model innovations
4. **Threat Assessment**: Note competitive risks:
   - Well-funded competitors with aggressive roadmaps
   - Market consolidation (acquisitions, partnerships)
   - Technology shifts (new platforms, standards)
   - Commoditization pressures

**Output Format**:
```markdown
## Competitive SWOT Summary

### [Competitor 1]
**Strengths**:
- [Market leader with 40% market share]
- [Enterprise-grade security and compliance]
- [Strong integration ecosystem (200+ integrations)]

**Weaknesses**:
- [Complex UI, steep learning curve (3.2/5 on ease-of-use)]
- [Expensive (avg $500/mo vs $200 industry avg)]
- [Slow to adopt modern features (no AI capabilities yet)]

**Market Position**: [Leader, but vulnerable to nimble challengers on UX and price]

### Opportunities for [Product]
- [Simplify UX for SMB market (competitor weakness)]
- [Offer usage-based pricing (vs per-seat model)]
- [Focus on [specific vertical] where competitors are generic]

### Threats
- [Competitor 2 raised $50M Series B, aggressively hiring]
- [Competitor 3 recently added [feature X], closing feature gap]
```

---

### Step 6: Strategic Positioning (15-20 min)

**Objective**: Map competitive positioning and identify white space

**Actions**:
1. **Positioning Dimensions**: Choose 2 key axes based on market, e.g.:
   - **Axis 1**: Simple/Easy ↔ Powerful/Advanced
   - **Axis 2**: Low Cost ↔ Premium/Enterprise
   - **Alternatives**: Generalist ↔ Specialist, Developer-focused ↔ Business-focused, Self-serve ↔ Sales-led
2. **Plot Competitors**: Based on research, position each competitor on the 2x2 grid
3. **Identify White Space**: Look for quadrants with few or no competitors
4. **Validate Fit**: Assess whether white space aligns with:
   - Product capabilities and strengths
   - Target audience needs
   - Business model and go-to-market strategy
5. **Positioning Recommendation**: Articulate where the product should position itself and why

**Output Format**:
```markdown
## Competitive Positioning Map

```
       Premium/Enterprise
              |
    [Comp 2]  |  [Comp 1]
              |  (market leader)
 Simple ------+------ Powerful
    [WHITE    |  [Comp 3]
     SPACE]   |  [Comp 4]
              |
         Low Cost
```

### Positioning Recommendation

**Target Position**: [Simple + Low Cost quadrant]

**Rationale**:
- White space opportunity: Only [Competitor 5] in this quadrant, but weak on [dimension]
- Aligned with product strengths: [Easy to use, quick setup, transparent pricing]
- Underserved audience: SMBs and startups priced out by [Competitor 1, 2]
- Differentiation angle: "Enterprise features at startup prices"

**Messaging Framework**:
- **Primary**: [Product] is the simplest way to [core value prop]
- **Secondary**: Get enterprise-grade [features] without enterprise complexity or cost
- **Proof points**: [5-min setup, $49/mo, 4.8/5 ease-of-use rating]
```

---

### Step 7: Competitive Strategy Report (20-25 min)

**Objective**: Synthesize findings into actionable strategic recommendations

**Actions**:
1. **Executive Summary**: Summarize competitive landscape in 3-5 bullet points
2. **Top Competitors Overview**: Brief profiles of 3-5 key competitors
3. **Feature Gap Priorities**: Rank must-have, should-have, nice-to-have competitive features
4. **Strategic Recommendations**: Provide 5-7 specific actions:
   - Features to build for competitive parity
   - Features to build for differentiation
   - Positioning and messaging recommendations
   - Pricing strategy adjustments
   - Go-to-market tactics
   - Partnership or ecosystem opportunities
   - Competitive risks to monitor
5. **Success Metrics**: Define KPIs to track competitive performance:
   - Win rate vs specific competitors
   - Feature parity score
   - Competitive win/loss reasons
   - Market share or SOV (share of voice)

**Output Format**:
```markdown
## Competitive Intelligence Report

### Executive Summary
- [Key finding 1: Market dominated by [X], opportunity in [Y]]
- [Key finding 2: Feature parity requires [A, B, C]]
- [Key finding 3: White space in [Z] positioning]
- [Key finding 4: Pricing is [X]% higher/lower than market avg]
- [Key finding 5: Main competitive advantage is [W]]

### Top 3 Competitors

#### 1. [Competitor 1] - Market Leader
- **Market Position**: 40% market share, enterprise-focused
- **Strengths**: [Feature breadth, compliance, brand]
- **Weaknesses**: [Price, complexity, slow innovation]
- **Threat Level**: 🔴 High (direct competitor, well-funded)
- **Strategy**: [Differentiate on simplicity and price]

#### 2. [Competitor 2] - Fast Follower
[Similar format]

#### 3. [Competitor 3] - Niche Player
[Similar format]

### Feature Gap Analysis

**Critical Gaps (Must-Have)**:
1. **[Feature X]**: Available in 4/5 competitors, table stakes for enterprise
   - Impact: High (deal-breaker in sales process)
   - Effort: Medium (2-3 sprints estimated)
   - Priority: P0 - Build in Q1

2. **[Feature Y]**: Standard in market, customers expect it
   - Impact: Medium (improves retention)
   - Effort: Low (1 sprint)
   - Priority: P1 - Build in Q1

**Differentiation Opportunities (Should-Have)**:
1. **[Feature Z]**: Unique feature, no competitor offers
   - Impact: High (major differentiator)
   - Effort: High (new paradigm, 1-2 quarters)
   - Priority: P1 - Prototype in Q2, launch Q3

**Nice-to-Have**:
- [Feature W]: Only in 1 competitor, limited demand signals

### Strategic Recommendations

#### 1. Achieve Feature Parity in Core Areas (Q1-Q2)
**Rationale**: Close critical gaps that cause lost deals
**Actions**:
- Build [Feature X, Y] by end of Q1
- Achieve 90% feature parity with top 2 competitors
- Track: Win rate vs [Competitor 1] (target: 30% → 45%)

#### 2. Differentiate on [Key Dimension] (Q2-Q3)
**Rationale**: White space in [simple + low-cost] positioning
**Actions**:
- Position as "easiest [category] for SMBs"
- Launch [differentiating feature Z]
- Messaging: "[Product] vs [Competitor 1]" comparison page
- Track: Brand awareness in SMB segment, feature Z adoption

#### 3. Optimize Pricing for Competitive Advantage (Q1)
**Rationale**: Competitors are 2-3x more expensive, price-sensitive segment underserved
**Actions**:
- Introduce $49/mo tier (vs competitor avg $150/mo)
- Keep free tier generous (10 users vs competitor avg 5)
- Annual discount: 20% (match market standard)
- Track: Free-to-paid conversion rate, price as win reason

#### 4. Build Integration Ecosystem (Q2-Q4)
**Rationale**: [Competitor 1] has 200 integrations, we have 15 - ecosystem is moat
**Actions**:
- Prioritize top 10 integrations (Slack, Zapier, etc.)
- Launch integration directory
- Partner with [complementary tools]
- Track: Integrations used per customer, integration as win reason

#### 5. Target Underserved Vertical: [e.g., Agencies] (Q3-Q4)
**Rationale**: Competitors are horizontal, agencies have unique needs
**Actions**:
- Add agency-specific features ([client management, white-labeling])
- Case studies and templates for agencies
- Agency-focused marketing campaigns
- Track: Agency customer % (target: 25% of new customers)

#### 6. Monitor Emerging Threats (Ongoing)
**Risks**:
- [Competitor 2] raised $50M, may acquire smaller players or price aggressively
- [Competitor 3] launching [competitive feature] in Q2 (per their roadmap)
- Open source alternative [X] gaining traction (5K GitHub stars, 2K/mo growth)

**Actions**:
- Monthly competitive intel check-ins
- Set Google Alerts for competitor news
- Track competitor feature releases
- Participate in industry forums/communities

#### 7. Win/Loss Analysis Program (Q1)
**Rationale**: Formalize competitive learning
**Actions**:
- Survey all lost deals for reasons
- Interview won deals for why they chose us
- Categorize: Feature gaps, price, trust, other
- Monthly competitive win/loss report
- Track: Win rate trend, top 3 loss reasons

### Success Metrics (6-12 months)

| Metric | Current | Target (6mo) | Target (12mo) |
|--------|---------|--------------|---------------|
| Overall win rate | 25% | 35% | 45% |
| Win rate vs [Comp 1] | 15% | 25% | 35% |
| Feature parity score | 65% | 85% | 90% |
| Price competitiveness | +50% vs avg | -10% vs avg | -20% vs avg |
| SOV (share of voice) | 5% | 10% | 15% |
| G2 rating | 4.2/5 | 4.5/5 | 4.6/5 |

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **Competitor coverage**: Researched 5-7 competitors (3-4 direct, 2-3 indirect)
- [ ] **Feature matrix**: Documented 20+ features across 5+ categories
- [ ] **Pricing data**: Captured pricing for all major competitors with tier breakdowns
- [ ] **Source citation**: All claims backed by URLs (websites, reviews, articles)
- [ ] **SWOT analysis**: Clear strengths, weaknesses, opportunities, threats for top 3 competitors
- [ ] **Positioning map**: 2x2 grid with competitors placed and white space identified
- [ ] **Actionable recommendations**: 5-7 specific, prioritized actions with success metrics
- [ ] **Evidence-based**: Findings grounded in web research, not assumptions
- [ ] **Formatted clearly**: Tables, lists, and sections for easy scanning

---

## Output Template

```markdown
# Competitive Intelligence Report: [Product Name]
*Generated: [Date]*

## Executive Summary
[3-5 key findings bullet points]

## Competitive Landscape
### Direct Competitors
[List with descriptions]

### Indirect Competitors
[List with descriptions]

## Feature Comparison Matrix
[Table with categories and features]

### Feature Gaps
**Where competitors lead**: [List]
**Where we lead**: [List]

## Value Proposition Analysis
[Table comparing messaging]

### Messaging Patterns
[Common themes, underserved themes, recommended positioning]

## Pricing Comparison
[Table with tiers and prices]

### Pricing Insights
[Model, ranges, value metrics, recommendation]

## Competitive SWOT Summary
### [Competitor 1]
**Strengths**: [List]
**Weaknesses**: [List]
**Market Position**: [Description]

[Repeat for top 3 competitors]

### Opportunities for [Product]
[List of opportunities]

### Threats
[List of threats]

## Strategic Positioning Map
[ASCII or description of 2x2 grid]

### Positioning Recommendation
[Target position, rationale, messaging framework]

## Strategic Recommendations
### 1. [Recommendation Title]
**Rationale**: [Why]
**Actions**: [Specific steps]
**Track**: [Metrics]

[Repeat for 5-7 recommendations]

## Success Metrics
[Table with current, 6-month, 12-month targets]

---

## Sources
[List all URLs referenced during research]
```

---

## Tips for Effective Competitive Intelligence

1. **Go beyond websites**: Check reviews, forums, social media for authentic user sentiment
2. **Screenshot key pages**: Competitor websites change; capture pricing, features, messaging
3. **Track over time**: Competitive intel is a snapshot; repeat quarterly to track shifts
4. **Talk to users**: Win/loss interviews provide insights web research can't
5. **Use the product**: Sign up for free trials to experience competitors firsthand
6. **Follow competitors**: Subscribe to newsletters, social media, release notes
7. **Be objective**: Acknowledge competitor strengths honestly; don't underestimate
8. **Focus on insights, not just data**: Raw feature counts matter less than strategic implications
9. **Update regularly**: Markets move fast; set calendar reminders for competitive reviews
10. **Share widely**: Competitive intel is valuable across sales, marketing, product, engineering

---

## Integration with Other Skills

This skill works well with:

- **product-evolution-analysis**: Use competitive gaps to inform roadmap priorities
- **improvement-proposals**: Translate competitive insights into specific feature proposals
- **persona-definition**: Understand how competitors segment and target users
- **changelog-creation**: Announce competitive feature parity in user-facing changelogs

---

*Use this skill whenever you need deep competitive insights to inform product strategy, roadmap planning, positioning, or go-to-market decisions.*
