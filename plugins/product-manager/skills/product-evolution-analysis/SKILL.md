---
name: product-evolution-analysis
description: Comprehensive 7-step framework to assess product current state, identify market opportunities, prioritize features using RICE, and create a strategic evolution roadmap with quarterly themes and success metrics
---

# Product Evolution Analysis Skill

Analyze a product's current state, market position, and growth opportunities to create a prioritized evolution roadmap with actionable recommendations.

## When to Use This Skill

Use this skill when you need to:
- Assess a product's current state and maturity
- Identify gaps between current capabilities and market needs
- Discover opportunities for product growth and improvement
- Prioritize features and initiatives using data-driven frameworks
- Create a strategic 3-12 month product roadmap
- Make informed decisions about product direction
- Align stakeholders on product priorities

## 7-Step Product Evolution Framework

### Step 1: Current State Assessment (15-20 min)

**Objective**: Understand what the product is today, its maturity, and recent trajectory

**Actions**:
1. **Repository Analysis**:
   - Read README.md, CHANGELOG.md, package.json/requirements.txt, docs/
   - Analyze commit history (frequency, contributors, recent focus areas)
   - Review open/closed issues and PRs (feature requests, bugs, discussions)
   - Examine file structure (frontend/backend, architecture patterns)
2. **Product Classification**:
   - **Type**: SaaS, open source, API, dev tool, mobile app, etc.
   - **Stage**: MVP (pre-product-market fit), Growth (scaling), Mature (optimizing)
   - **Business model**: Freemium, paid, open-core, sponsorship, etc.
3. **Feature Inventory**: List all current features (from README, docs, code)
4. **Technical Assessment**:
   - Stack and technologies used
   - Code quality indicators (tests, docs, linting)
   - Technical debt signals (TODOs, deprecated code, issue labels)
5. **Activity Metrics**:
   - GitHub stars, forks, contributors
   - Release frequency and versioning
   - Community engagement (issues, discussions, PRs)

**Output Format**:
```markdown
## Current State Assessment

### Product Overview
- **Name**: [Product Name]
- **Type**: [SaaS/Open Source/API/Dev Tool/etc.]
- **Category**: [E.g., Project Management, Data Visualization, CI/CD, etc.]
- **Stage**: [MVP/Growth/Mature]
- **Tech Stack**: [Languages, frameworks, infrastructure]

### Core Features (Current)
1. **[Feature Category]**: [Feature 1], [Feature 2], [Feature 3]
2. **[Feature Category]**: [Feature 4], [Feature 5]
3. **[Feature Category]**: [Feature 6], [Feature 7]

### Maturity Indicators
- **Development Activity**: [Active/Moderate/Low] ([X commits/month avg])
- **Community**: [Y stars, Z forks, W contributors]
- **Release Cadence**: [Weekly/Monthly/Quarterly]
- **Documentation**: [Excellent/Good/Needs Improvement]
- **Test Coverage**: [High/Medium/Low/Unknown]
- **Technical Debt**: [Low/Moderate/High] (signals: [examples])

### Recent Trajectory (Last 3-6 Months)
- [Key development focus areas from commits/PRs]
- [Major features added or in progress]
- [Most requested features from issues]
- [Pain points or recurring bug themes]
```

---

### Step 2: Market Context Discovery (15-20 min)

**Objective**: Understand the market category, trends, competitors, and opportunities

**Actions**:
1. **Market Category Research**:
   - Web search: "[product category] market trends 2025"
   - Web search: "[product category] tools comparison"
   - Identify market size, growth rate, key players
2. **Competitive Landscape**:
   - Identify 3-5 direct competitors
   - Note their key features and positioning
   - Identify market leader and emerging challengers
3. **Market Trends**:
   - Emerging technologies (AI, real-time, mobile-first, etc.)
   - User behavior shifts (self-serve, collaboration, integrations)
   - Industry-specific trends (compliance, privacy, open source)
4. **Opportunity Signals**:
   - Underserved user segments
   - Feature gaps across competitors
   - New use cases or verticals
   - Platform shifts (e.g., mobile, edge computing, AI)

**Output Format**:
```markdown
## Market Context

### Market Category
- **Category**: [E.g., "Project Management Software" or "Static Site Generators"]
- **Market Size**: [TAM if available, e.g., "$10B by 2025"]
- **Growth Rate**: [E.g., "15% CAGR"]
- **Maturity**: [Emerging/Growing/Mature/Consolidating]

### Competitive Landscape
1. **[Competitor 1]** (Market Leader): [Key strengths, features, positioning]
2. **[Competitor 2]** (Fast Follower): [Key strengths, features, positioning]
3. **[Competitor 3]** (Niche Player): [Key strengths, features, positioning]

### Market Trends (2025)
- **Trend 1**: [E.g., "AI-powered automation" - How competitors are adopting]
- **Trend 2**: [E.g., "Real-time collaboration" - Market expectation]
- **Trend 3**: [E.g., "Privacy-first design" - Emerging requirement]

### Opportunity Signals
- [Underserved segment: E.g., "SMBs priced out of enterprise tools"]
- [Feature gap: E.g., "No competitor offers [specific feature]"]
- [Vertical opportunity: E.g., "Healthcare vertical has unique needs"]
- [Platform shift: E.g., "Mobile-first usage growing 40% YoY"]
```

---

### Step 3: User Journey Mapping (15-20 min)

**Objective**: Understand how users interact with the product, identify pain points and drop-offs

**Actions**:
1. **User Flow Analysis**:
   - Identify primary user journeys (from docs, README, UI/UX)
   - Map: Discovery → Onboarding → Core Loop → Advanced Usage → Retention
2. **Onboarding Assessment**:
   - Time to first value (TTFV)
   - Complexity of setup (steps, dependencies, configuration)
   - Aha moment (when user gets core value)
3. **Core Loop**: Identify the repeated user action that delivers value
4. **Pain Point Discovery**:
   - Analyze GitHub issues for user complaints
   - Look for friction points (complex workflows, missing features, bugs)
   - Identify drop-off points (where users might abandon)
5. **Jobs-to-be-Done**: What jobs do users hire this product to do?
   - Functional jobs (tasks to complete)
   - Emotional jobs (how they want to feel)
   - Social jobs (how they want to be perceived)

**Output Format**:
```markdown
## User Journey Analysis

### Primary User Journey
1. **Discovery**: [How users find the product]
   - Channels: [GitHub, search, word-of-mouth, etc.]
   - First impression: [What they see on README/landing page]

2. **Onboarding**: [Getting started experience]
   - Time to first value: [Estimate, e.g., "5 minutes" or "2 hours"]
   - Steps required: [Installation, config, first usage]
   - Complexity: [Low/Medium/High]
   - Aha moment: [When does core value click?]

3. **Core Loop**: [Repeated valuable action]
   - Primary workflow: [E.g., "Create project → Add tasks → Assign → Track"]
   - Frequency: [Daily/Weekly/Monthly]
   - Value delivered: [Outcome user achieves]

4. **Advanced Usage**: [Power user features]
   - [Advanced feature 1, 2, 3]
   - Adoption: [High/Medium/Low based on signals]

5. **Retention**: [Why users stay]
   - Lock-in factors: [Data, integrations, habits, network effects]
   - Churn risks: [Missing features, competitors, complexity]

### Pain Points & Friction
- **Onboarding**: [E.g., "Setup requires 10 steps and 20min"]
- **Core workflow**: [E.g., "No bulk actions, must repeat task 10 times"]
- **Integrations**: [E.g., "No Slack integration, manual copy-paste"]
- **Performance**: [E.g., "Slow for large datasets (500ms+ load times)"]
- **Missing features**: [E.g., "No mobile app, desktop-only"]

### Jobs-to-be-Done
**Functional Jobs**:
- [E.g., "Track progress on multiple projects"]
- [E.g., "Collaborate with team members"]

**Emotional Jobs**:
- [E.g., "Feel organized and in control"]
- [E.g., "Reduce anxiety about missing deadlines"]

**Social Jobs**:
- [E.g., "Be seen as a reliable team member"]
- [E.g., "Impress clients with professionalism"]
```

---

### Step 4: Gap Analysis (15-20 min)

**Objective**: Identify gaps between current capabilities and user needs/market expectations

**Actions**:
1. **Capability vs Need Matrix**:
   - List user needs (from journey mapping, issues, competitor features)
   - Assess current capability: Excellent / Good / Basic / Missing
2. **Competitive Feature Gaps**:
   - Features competitors have that the product lacks
   - Prioritize: Table stakes (must-have) vs nice-to-have
3. **Technical Debt Audit**:
   - Review TODO comments, issue labels like "tech-debt" or "refactor"
   - Identify: Performance issues, scalability limits, security concerns
   - Assess impact on user experience and development velocity
4. **Innovation Opportunities**:
   - Features no competitor offers (blue ocean)
   - Emerging tech to adopt early (AI, real-time, etc.)
   - New use cases or workflows to enable

**Output Format**:
```markdown
## Gap Analysis

### User Needs vs Capabilities

| User Need | Importance | Current Capability | Gap Level | Notes |
|-----------|------------|-------------------|-----------|-------|
| [Need 1] | High | Basic | 🔴 Large | [Missing key features X, Y] |
| [Need 2] | High | Good | 🟡 Medium | [Works but UX needs improvement] |
| [Need 3] | Medium | Excellent | 🟢 None | [Competitive strength] |
| [Need 4] | High | Missing | 🔴 Large | [Critical gap, users requesting] |

### Competitive Feature Gaps

**Table Stakes (Must Close)**:
1. **[Feature X]**: 4/5 competitors offer, users expect it, blocks enterprise deals
2. **[Feature Y]**: Industry standard, absence causes confusion

**Differentiation Opportunities**:
1. **[Feature Z]**: No competitor offers, solves common pain point [P]
2. **[Feature W]**: Unique approach to [problem], potential moat

**Nice-to-Have**:
- [Feature V]: Only 1 competitor offers, limited demand

### Technical Debt Impact

| Debt Item | Impact on Users | Impact on Dev Velocity | Priority |
|-----------|----------------|------------------------|----------|
| [E.g., No test coverage] | Medium (bugs reach prod) | High (fear of changes) | P1 |
| [E.g., Monolithic architecture] | Low (performance ok) | High (hard to add features) | P2 |
| [E.g., Legacy dependencies] | High (security risks) | Medium (upgrade effort) | P0 |

### Innovation Opportunities

1. **[Opportunity 1]**: [E.g., "AI-powered suggestions" - No competitor offers, high user value]
2. **[Opportunity 2]**: [E.g., "Real-time collaboration" - Market trend, competitive advantage]
3. **[Opportunity 3]**: [E.g., "Mobile-first redesign" - Platform shift, 40% of users mobile]
```

---

### Step 5: Opportunity Prioritization (20-25 min)

**Objective**: Rank opportunities using RICE framework and value-complexity matrix

**Actions**:
1. **Opportunity Generation**: List 15-20 opportunities from:
   - Feature gaps (from competitive analysis)
   - User pain points (from issues, journey mapping)
   - Technical debt (impacting users or velocity)
   - Innovation ideas (new capabilities)
2. **RICE Scoring**: For each opportunity, estimate:
   - **Reach**: How many users benefit? (per quarter)
     - Low: <10% of users
     - Medium: 10-50% of users
     - High: >50% of users
   - **Impact**: How much does it improve their experience? (per user)
     - 0.25 = Minimal
     - 0.5 = Low
     - 1 = Medium
     - 2 = High
     - 3 = Massive
   - **Confidence**: How certain are we? (%)
     - 50% = Low confidence (hypothesis)
     - 80% = Medium (some data)
     - 100% = High (validated need)
   - **Effort**: Development time (person-months)
     - 0.5 = <1 week
     - 1 = 1-2 weeks
     - 2 = 2-4 weeks
     - 4 = 1-2 months
     - 8+ = >2 months
   - **RICE Score** = (Reach × Impact × Confidence) / Effort
3. **Value-Complexity Matrix**: Plot opportunities on 2x2 grid:
   - **Y-axis**: User/Business Value (Low to High)
   - **X-axis**: Implementation Complexity (Low to High)
   - **Quadrants**:
     - High Value, Low Complexity = Quick Wins (do first)
     - High Value, High Complexity = Strategic Bets (plan carefully)
     - Low Value, Low Complexity = Fill-ins (do if time)
     - Low Value, High Complexity = Avoid (deprioritize)
4. **Strategic Alignment**: Filter by:
   - Alignment with business goals (revenue, growth, retention)
   - Competitive necessity (must-have vs nice-to-have)
   - Technical feasibility (dependencies, skills, infrastructure)

**Output Format**:
```markdown
## Opportunity Prioritization

### RICE Scoring (Top 15 Opportunities)

| Rank | Opportunity | Reach | Impact | Confidence | Effort | RICE Score | Category |
|------|-------------|-------|--------|------------|--------|------------|----------|
| 1 | [Opportunity 1] | 1000 | 2 | 100% | 2 | 1000 | Feature |
| 2 | [Opportunity 2] | 500 | 3 | 80% | 1 | 1200 | Innovation |
| 3 | [Opportunity 3] | 2000 | 1 | 100% | 4 | 500 | Feature Gap |
| 4 | [Opportunity 4] | 300 | 2 | 50% | 0.5 | 600 | Quick Win |
| ... | ... | ... | ... | ... | ... | ... | ... |

**RICE Calculation Example**:
- Opportunity 1: (1000 reach × 2 impact × 100% confidence) / 2 effort = 1000

### Value-Complexity Matrix

```
High Value    |                    |
              | [Strategic Bets]   | [Quick Wins]
              | - Opp 2 (RICE 1200)| - Opp 4 (RICE 600)
              | - Opp 5 (RICE 800) | - Opp 6 (RICE 550)
              |                    |
--------------+--------------------+-------------------
              | [Avoid]            | [Fill-ins]
Low Value     | - Opp 14 (RICE 50) | - Opp 12 (RICE 200)
              |                    | - Opp 13 (RICE 150)
              |                    |
         Low Complexity      High Complexity
```

### Prioritization Tiers

**Tier 1: Must-Do (Q1)**
1. **[Opportunity 4]** (RICE: 600): [Quick win, closes critical gap]
2. **[Opportunity 1]** (RICE: 1000): [Table stakes feature, competitive parity]
3. **[Opportunity 6]** (RICE: 550): [High user impact, low effort]

**Tier 2: Should-Do (Q2)**
1. **[Opportunity 2]** (RICE: 1200): [Strategic bet, major differentiator]
2. **[Opportunity 3]** (RICE: 500): [Scales product to larger customers]

**Tier 3: Nice-to-Have (Q3-Q4)**
1. **[Opportunity 8]** (RICE: 350): [Polish, improves existing feature]
2. **[Opportunity 10]** (RICE: 300): [Niche request, low reach]

**Deprioritized (Not Now)**
- [Opportunity 14, 15]: [Low value, high effort, avoid]
```

---

### Step 6: Evolution Roadmap (20-25 min)

**Objective**: Create a 3-12 month roadmap with quarterly themes, milestones, and metrics

**Actions**:
1. **Define North Star Metric**: Single metric that captures core value
   - SaaS: Active users, usage frequency, revenue
   - Open source: Contributors, downloads, integrations
   - Dev tools: Adoption rate, time-to-value
2. **Quarterly Themes**: Assign themes to each quarter based on priorities
   - Q1: [E.g., "Feature Parity & Quick Wins"]
   - Q2: [E.g., "Differentiation & Scale"]
   - Q3: [E.g., "Polish & Growth"]
   - Q4: [E.g., "Innovation & Expansion"]
3. **Roadmap Structure**: For each quarter, define:
   - **Theme**: Strategic focus
   - **Initiatives**: 3-5 major initiatives (from prioritized opportunities)
   - **Outcomes**: Expected results (metrics, capabilities)
   - **Milestones**: Key deliverables and dates
4. **Success Metrics**: Define KPIs for each initiative
5. **Dependencies & Risks**: Note blockers, dependencies, uncertainties

**Output Format**:
```markdown
## Product Evolution Roadmap

### North Star Metric
**[Metric Name]**: [Definition]
- **Current**: [X]
- **6-month target**: [Y]
- **12-month target**: [Z]
- **Rationale**: [Why this metric captures product success]

### Q1 (Jan-Mar 2025): [Theme Name, e.g., "Foundation & Quick Wins"]

**Strategic Focus**: Close critical gaps, achieve table stakes, demonstrate momentum

**Initiatives**:
1. **[Initiative 1: E.g., "Feature Parity Sprint"]**
   - Scope: Build [Feature X, Y, Z] to match competitor capabilities
   - Impact: Close 3 critical gaps causing lost deals
   - Success Metrics: Feature usage by 60% of users within 2 weeks of launch
   - Effort: 6 weeks, 2 engineers
   - Dependencies: None
   - Risks: [Feature X] requires API changes, may slip to early Q2

2. **[Initiative 2: E.g., "Onboarding Overhaul"]**
   - Scope: Reduce time-to-value from 2 hours to 15 minutes
   - Impact: Improve activation rate (target: 40% → 60%)
   - Success Metrics: Time-to-first-value, activation rate, user feedback scores
   - Effort: 4 weeks, 1 engineer + 1 designer
   - Dependencies: None
   - Risks: Low; mostly UX improvements

3. **[Initiative 3: E.g., "Performance Optimization"]**
   - Scope: Address tech debt causing slow load times (>2s)
   - Impact: Improve user satisfaction, reduce churn
   - Success Metrics: P95 load time <500ms, bounce rate decrease
   - Effort: 3 weeks, 1 engineer
   - Dependencies: None
   - Risks: May uncover additional technical debt

**Key Milestones**:
- Week 2: [Milestone 1]
- Week 6: [Milestone 2]
- Week 10: [Milestone 3]
- End of Q1: [Initiative 1, 2, 3 launched]

**Expected Outcomes**:
- Feature parity: 85% → 95% vs top competitors
- Activation rate: 40% → 60%
- P95 load time: 2s → 500ms
- North Star Metric: [X → Y]

---

### Q2 (Apr-Jun 2025): [Theme Name, e.g., "Differentiation & Growth"]

**Strategic Focus**: Build unique capabilities, differentiate from competitors, accelerate growth

**Initiatives**:
1. **[Initiative 1: E.g., "AI-Powered Automation"]**
   - Scope: [Details]
   - Impact: [User value, business value]
   - Success Metrics: [KPIs]
   - Effort: [Time, resources]

2. **[Initiative 2]**: [Similar format]

3. **[Initiative 3]**: [Similar format]

**Key Milestones**: [List]

**Expected Outcomes**: [Metrics, capabilities]

---

### Q3 (Jul-Sep 2025): [Theme Name]
[Similar format]

---

### Q4 (Oct-Dec 2025): [Theme Name]
[Similar format]

---

### Roadmap Dependencies & Risks

**Cross-Quarter Dependencies**:
- Q2 Initiative 1 depends on Q1 Initiative 3 completion
- Q3 Initiative 2 requires Q2 infrastructure work

**Key Risks**:
- **Resource constraints**: Roadmap assumes 2-3 engineers; delays if team size changes
- **Competitive response**: [Competitor X] may launch [Feature Y] in Q2, changing priorities
- **Technical complexity**: Q2 Initiative 1 is unproven tech, may require more time
- **Market shifts**: If [trend Z] accelerates, may need to reprioritize Q3-Q4

**Mitigation Strategies**:
- Monthly roadmap reviews to adjust priorities
- Buffer time (20%) in effort estimates
- Parallel track exploration of Q3-Q4 initiatives
- Continuous competitive monitoring
```

---

### Step 7: Recommendation Report (15-20 min)

**Objective**: Synthesize analysis into executive summary with top recommendations

**Actions**:
1. **Executive Summary**: 5-7 key findings in bullet points
2. **Top 5 Opportunities**: Highlight highest-priority opportunities with:
   - What it is
   - Why it matters (user impact, business impact)
   - How to execute (scope, effort, timeline)
   - How to measure success (metrics)
3. **Strategic Positioning**: Recommended market position and messaging
4. **Next Steps**: Immediate actions to take (next 2-4 weeks)
5. **Resource Requirements**: Team, budget, tools needed
6. **Decision Points**: Key decisions stakeholders need to make

**Output Format**:
```markdown
## Executive Summary: Product Evolution Recommendations

### Key Findings
1. **[Finding 1]**: [E.g., "Feature parity gap with top competitors causing 30% of lost deals"]
2. **[Finding 2]**: [E.g., "Onboarding takes 2 hours vs 15 min industry avg, hurting activation"]
3. **[Finding 3]**: [E.g., "Market opportunity in [vertical/segment] with 10x fewer competitors"]
4. **[Finding 4]**: [E.g., "AI automation trend growing 50% YoY, competitors slow to adopt"]
5. **[Finding 5]**: [E.g., "Technical debt in [area] limiting development velocity by 30%"]

### Top 5 Recommended Opportunities

#### 1. [Opportunity Name] (RICE Score: 1200)
**What**: [Brief description]

**Why it Matters**:
- **User Impact**: [E.g., "Reduces manual work by 80%, top requested feature"]
- **Business Impact**: [E.g., "Estimated +15% conversion rate, +$500K ARR"]
- **Strategic Value**: [E.g., "Key differentiator, creates moat vs competitors"]

**How to Execute**:
- **Scope**: [E.g., "Build [feature components A, B, C], integrate with [system]"]
- **Effort**: [E.g., "8 weeks, 2 engineers, 1 designer"]
- **Timeline**: [E.g., "Q2 2025 (Apr-Jun)"]
- **Dependencies**: [E.g., "None" or "Requires Q1 infrastructure work"]

**Success Metrics**:
- Feature adoption: 70% of active users within 1 month
- Usage frequency: 5x per week average
- User satisfaction: 4.5/5 rating
- Business impact: +15% conversion rate

---

#### 2. [Opportunity Name] (RICE Score: 1000)
[Similar format]

---

#### 3. [Opportunity Name] (RICE Score: 800)
[Similar format]

---

#### 4. [Opportunity Name] (RICE Score: 600)
[Similar format]

---

#### 5. [Opportunity Name] (RICE Score: 550)
[Similar format]

---

### Strategic Positioning Recommendation

**Recommended Position**: [E.g., "The simplest [category] for [target audience]"]

**Rationale**:
- Market gap in [quadrant] of positioning map (simple + affordable)
- Differentiation from [Competitor 1] (complex) and [Competitor 2] (expensive)
- Aligned with product strengths (ease of use, fast onboarding, transparent pricing)

**Key Messages**:
- **Primary**: [E.g., "Get [outcome] in 15 minutes, not 2 hours"]
- **Secondary**: [E.g., "Enterprise features at startup prices"]
- **Proof Points**: [E.g., "4.8/5 ease-of-use rating, $49/mo vs $150 industry avg"]

---

### Immediate Next Steps (Next 2-4 Weeks)

**Week 1-2**:
- [ ] Socialize this roadmap with stakeholders (eng, sales, marketing)
- [ ] Validate top 3 opportunities with 5-10 users (interviews or surveys)
- [ ] Begin technical scoping for Q1 initiatives
- [ ] Set up analytics to track north star metric and initiative KPIs

**Week 3-4**:
- [ ] Finalize Q1 roadmap with engineering team
- [ ] Create detailed specs for top 2 initiatives
- [ ] Start design work for [Initiative 2]
- [ ] Launch competitive monitoring system (alerts, tracking)

---

### Resource Requirements

**Team**:
- 2-3 full-time engineers
- 1 designer (50% time)
- 1 product manager (you or dedicated PM)
- Optional: 1 data analyst for metrics tracking

**Budget**:
- Engineering time: [Estimate based on team]
- Tools: Analytics ($200/mo), competitive intel tools ($100/mo)
- User research: $5K for interviews/surveys (optional)

**Tools & Infrastructure**:
- Analytics platform for KPI tracking (if not already in place)
- Feature flag system for gradual rollouts
- User feedback tool (e.g., in-app surveys, NPS)

---

### Key Decisions Needed

**Decision 1**: Prioritization approval
- **Question**: Approve Q1-Q2 roadmap priorities as recommended?
- **Options**: (A) Approve as-is, (B) Adjust priorities, (C) Defer for more research
- **Recommendation**: (A) Approve - priorities are data-driven and address critical gaps
- **Deadline**: [Date, e.g., "End of week"]

**Decision 2**: Resource allocation
- **Question**: Can we commit 2-3 engineers to product initiatives?
- **Options**: (A) Yes, dedicate team, (B) Partial (1-2 engineers), (C) No, maintain only
- **Recommendation**: (A) Dedicate team - roadmap assumes this capacity
- **Deadline**: [Date]

**Decision 3**: Strategic positioning
- **Question**: Pursue "[positioning]" or alternative positioning?
- **Options**: (A) Recommended positioning, (B) Alternative [describe], (C) Defer
- **Recommendation**: (A) Aligns with market gap and product strengths
- **Deadline**: [Date]

---

## Appendices

### Appendix A: Full RICE Scoring (All 20+ Opportunities)
[Complete table if needed]

### Appendix B: Competitive Feature Matrix
[Link to competitive-intelligence skill output or include abbreviated version]

### Appendix C: User Persona Profiles
[Link to persona-definition skill output or include summaries]

### Appendix D: Data Sources
- Repository analysis: [GitHub URL]
- Competitive research: [List of URLs]
- Market research: [List of URLs]
- User feedback: [Issues, surveys, interviews]
```

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **Current state**: Documented features, tech stack, maturity, activity metrics
- [ ] **Market context**: Researched 3-5 competitors, trends, opportunities
- [ ] **User journey**: Mapped discovery → retention, identified pain points
- [ ] **Gap analysis**: Compared capabilities vs needs, competitive features vs current features
- [ ] **Prioritization**: RICE scores for 15+ opportunities, value-complexity matrix plotted
- [ ] **Roadmap**: Quarterly themes, 3-5 initiatives per quarter, milestones, metrics
- [ ] **Recommendations**: Top 5 opportunities with clear rationale, impact, effort, metrics
- [ ] **Evidence-based**: All claims backed by repository analysis, web research, or data
- [ ] **Actionable**: Specific next steps with timelines and owners
- [ ] **Formatted clearly**: Headings, tables, bullet points for easy scanning

---

## Output Template

Use this template for the final report:

```markdown
# Product Evolution Analysis: [Product Name]
*Generated: [Date]*

## Executive Summary: Product Evolution Recommendations
[5-7 key findings]

### Top 5 Recommended Opportunities
[Each with What, Why, How, Success Metrics]

### Strategic Positioning Recommendation
[Position, rationale, key messages]

### Immediate Next Steps
[2-4 week action plan]

---

## Current State Assessment
[Product overview, features, maturity, trajectory]

## Market Context
[Category, competitors, trends, opportunities]

## User Journey Analysis
[Discovery → retention, pain points, JTBD]

## Gap Analysis
[User needs vs capabilities, competitive gaps, technical debt, innovation opportunities]

## Opportunity Prioritization
[RICE scoring table, value-complexity matrix, prioritization tiers]

## Product Evolution Roadmap
[North star metric, Q1-Q4 themes, initiatives, milestones, outcomes]

---

## Recommendations Summary
[Detailed top 5 opportunities]

## Resource Requirements
[Team, budget, tools]

## Key Decisions Needed
[Decision points for stakeholders]

---

## Appendices
[Full data, sources, extended analyses]
```

---

## Tips for Effective Product Evolution Analysis

1. **Start broad, then narrow**: Understand full landscape before diving into specific opportunities
2. **Ground in evidence**: Every recommendation should tie back to data from the repo, users, or market
3. **Prioritize ruthlessly**: Not everything can be P0; use frameworks to make hard choices
4. **Think in bets**: Some initiatives are high-confidence (quick wins), others are bets (innovation)
5. **Balance short and long term**: Mix quick wins (Q1) with strategic bets (Q2-Q4)
6. **Involve stakeholders early**: Socialize findings before finalizing to build buy-in
7. **Set measurable goals**: Every initiative needs clear success metrics
8. **Plan for unknowns**: Buffer effort estimates by 20%, expect some priorities to shift
9. **Revisit regularly**: Markets and products evolve; update analysis quarterly
10. **Tell a story**: Connect current state → gaps → opportunities → roadmap → outcomes

---

## Integration with Other Skills

This skill works well with:

- **competitive-intelligence**: Deep competitive research informs gap analysis and positioning
- **persona-definition**: User personas inform journey mapping and opportunity prioritization
- **improvement-proposals**: Translate high-level roadmap into specific feature proposals
- **changelog-creation**: Communicate roadmap progress to users through compelling changelogs

---

*Use this skill whenever you need a comprehensive product strategy and roadmap for the next 3-12 months.*
