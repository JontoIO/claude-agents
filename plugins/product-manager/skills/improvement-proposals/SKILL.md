---
name: improvement-proposals
description: Generate and prioritize improvement proposals using 6-step framework including opportunity mining, impact assessment, RICE scoring, value-complexity matrix, and detailed business cases with implementation guidance
---

# Improvement Proposal Generation Skill

Generate a prioritized list of product improvements with detailed business cases, impact estimates, and implementation guidance using data-driven prioritization frameworks.

## When to Use This Skill

Use this skill when you need to:
- Generate ideas for product improvements and new features
- Prioritize improvements using RICE, ICE, or value-complexity frameworks
- Create business cases for feature proposals
- Assess impact vs effort for potential initiatives
- Build a backlog of validated improvement opportunities
- Make go/no-go decisions on feature investments
- Communicate product improvement plans to stakeholders

## 6-Step Improvement Proposal Framework

### Step 1: Opportunity Mining (15-20 min)

**Objective**: Discover improvement opportunities from multiple sources

**Actions**:
1. **Technical Debt Analysis**:
   - Search codebase for TODO, FIXME, HACK comments
   - Review issues labeled "tech-debt", "refactor", "bug"
   - Identify performance bottlenecks, scalability limits, security issues
   - Assess impact on user experience and developer velocity
2. **Feature Request Analysis**:
   - Review GitHub issues, discussions, and PRs
   - Look for patterns in user requests (multiple users asking for same thing)
   - Categorize by frequency and intensity of requests
   - Note which features are mentioned in competitive contexts ("Competitor X has this")
3. **User Experience Friction**:
   - Analyze common user workflows for friction points
   - Look for multi-step processes that could be automated
   - Identify error-prone areas or confusing UX
   - Review onboarding experience for drop-off points
4. **Competitive Feature Gaps**:
   - Compare features vs top 3-5 competitors
   - Identify table stakes features (must-have for market)
   - Spot differentiating features (unique to competitors)
   - Look for emerging trends competitors are adopting
5. **Innovation Opportunities**:
   - Identify emerging technologies to adopt (AI, real-time, etc.)
   - Look for new use cases or workflows to enable
   - Consider platform expansions (mobile, API, integrations)
   - Explore adjacent problem spaces

**Output Format**:
```markdown
## Opportunity Mining

### Technical Debt Opportunities

**Performance & Scalability**:
1. **[Issue]**: Database queries slow for datasets >10K items (500ms+ load times)
   - Source: Issues #123, #145, user complaints in discussions
   - Impact: User frustration, churn risk for power users
   - Signals: 15 issues mentioning "slow", 3.2/5 performance rating

2. **[Issue]**: Monolithic architecture makes feature development slow
   - Source: Engineering team feedback, 30% of sprint time on refactoring
   - Impact: Reduced development velocity, delayed features
   - Signals: Average PR time 2 weeks (industry avg: 3 days)

**Security & Reliability**:
3. **[Issue]**: No rate limiting on API endpoints
   - Source: Security audit, industry best practice
   - Impact: Risk of abuse, potential downtime from DDoS
   - Signals: 2 incidents in past 6 months

### Feature Request Opportunities

**High Frequency (10+ requests)**:
1. **Bulk operations**: Allow actions on multiple items at once
   - Requests: Issues #89, #112, #145, #203 (14 total)
   - User context: "Have to repeat same action 50 times, very tedious"
   - Competitors: 4/5 competitors offer this

2. **Real-time collaboration**: See changes from teammates live
   - Requests: Issues #67, #91, #156, #187 (12 total)
   - User context: "Refresh manually to see updates, confusing"
   - Competitors: 3/5 competitors offer this

**Medium Frequency (5-9 requests)**:
3. **Mobile app**: iOS/Android app for on-the-go access
   - Requests: Issues #45, #78, #134 (7 total)
   - User context: "Need to check status while away from desk"
   - Competitors: 2/5 competitors have mobile apps

### User Experience Friction

**Onboarding Friction**:
1. **Setup complexity**: 10-step setup process takes 2 hours
   - Evidence: Activation rate 35% (industry avg: 60%)
   - User feedback: "Too complicated, gave up halfway"
   - Opportunity: Reduce to 3 steps, 15-minute setup

2. **Unclear value proposition**: Users don't understand benefits until day 3-5
   - Evidence: 60% churn within first week
   - User feedback: "Didn't know what I was supposed to do"
   - Opportunity: Interactive tutorial, sample data, templates

**Workflow Friction**:
3. **No keyboard shortcuts**: Mouse-only interface slows power users
   - Evidence: Power users average 30 actions/day, could be 100+ with shortcuts
   - User feedback: "Wish I could do everything with keyboard"
   - Opportunity: Implement common shortcuts (Cmd+K, vim bindings)

### Competitive Feature Gaps

**Table Stakes (Must-Have)**:
1. **SSO / SAML**: Enterprise authentication
   - Competitive status: 5/5 competitors offer
   - User impact: Blocking 20% of enterprise deals
   - Market expectation: Required for enterprise sales

2. **Webhooks / API**: Programmatic access and integrations
   - Competitive status: 4/5 competitors offer
   - User impact: 30% of users asking for integrations
   - Market expectation: Standard for developer tools

**Differentiation (Unique)**:
3. **AI-powered suggestions**: Auto-suggest actions based on patterns
   - Competitive status: 0/5 competitors offer (yet)
   - User impact: Could save 50% of manual work
   - Market opportunity: Emerging trend, first-mover advantage

### Innovation Opportunities

**Emerging Technologies**:
1. **AI/ML Integration**: Leverage LLMs for automation and insights
   - Examples: Auto-categorization, smart search, content generation
   - Market trend: 50% YoY growth in AI-powered tools
   - Potential: Major differentiator, reduces manual work by 80%

2. **Real-time Sync**: WebSocket-based live updates
   - Examples: Collaborative editing, live notifications
   - Market trend: User expectation shifting to real-time
   - Potential: Improves UX, modern competitive parity

**New Use Cases**:
3. **[Vertical] Specialization**: Tailor product for specific industry
   - Example: Healthcare workflows, compliance features
   - Market opportunity: 10x fewer competitors in vertical
   - Potential: Higher willingness to pay, easier positioning

**Platform Expansion**:
4. **Mobile-First Redesign**: Native mobile apps
   - Trend: 40% of users accessing via mobile (up from 20% last year)
   - Potential: Reach new user segment, improve retention
```

---

### Step 2: Proposal Ideation (10-15 min)

**Objective**: Generate 10-15 specific improvement proposals across categories

**Actions**:
1. **Synthesize Opportunities**: Review all mined opportunities
2. **Generate Proposals**: For each opportunity, create a specific proposal
   - What: Clear description of the improvement
   - Why: User pain point or business opportunity it addresses
   - How: High-level approach (without deep technical design)
3. **Categorize Proposals**:
   - **Features**: New capabilities users can use
   - **Enhancements**: Improvements to existing features
   - **Technical**: Infrastructure, performance, security (user-visible impact)
   - **UX/Polish**: Usability improvements, design refinements
   - **Platform**: Mobile, API, integrations, ecosystem
4. **Keep Proposals Focused**: Each proposal should be a discrete unit of work (ideally shippable independently)

**Output Format**:
```markdown
## Improvement Proposals (15 Ideas)

### Features (New Capabilities)

**Proposal 1: Bulk Operations**
- **What**: Allow users to select multiple items and perform actions (delete, move, tag) on all at once
- **Why**: Users manually repeat actions 10-50 times, causing frustration and wasted time
- **How**: Add checkbox selection UI, bulk action menu, background job processing

**Proposal 2: Real-Time Collaboration**
- **What**: Enable live updates when teammates make changes, no manual refresh needed
- **Why**: Current manual refresh causes confusion about latest state and missed updates
- **How**: WebSocket connection for live updates, operational transforms for conflict resolution

**Proposal 3: AI-Powered Smart Suggestions**
- **What**: Automatically suggest next actions based on user behavior patterns
- **Why**: Users repeat common workflows; AI could predict and automate 50% of repetitive tasks
- **How**: Integrate LLM API, train on user action patterns, surface suggestions in UI

### Enhancements (Improvements to Existing)

**Proposal 4: Advanced Search & Filters**
- **What**: Add boolean operators, saved searches, and faceted filtering
- **Why**: Current basic search fails to find items, users rely on manual scanning
- **How**: Enhance search engine (Elasticsearch?), add filter UI, save search presets

**Proposal 5: Keyboard Shortcuts & Command Palette**
- **What**: Implement Cmd+K command palette and common keyboard shortcuts
- **Why**: Power users want faster navigation, mouse-only slows workflow
- **How**: Hotkey library (e.g., cmdk), map actions to shortcuts, searchable command palette

**Proposal 6: Performance Optimization (Large Datasets)**
- **What**: Reduce load times from 2s to <500ms for datasets >10K items
- **Why**: Power users with large datasets experiencing frustration and considering alternatives
- **How**: Database query optimization, pagination, virtual scrolling, caching

### Technical (Infrastructure/Platform)

**Proposal 7: API Rate Limiting & Throttling**
- **What**: Implement rate limits on API endpoints to prevent abuse
- **Why**: Risk of DDoS, API abuse, service degradation for all users
- **How**: Add rate limiting middleware (Redis-based), tiered limits by plan

**Proposal 8: Webhooks & API Extensibility**
- **What**: Allow users to subscribe to events via webhooks, build custom integrations
- **Why**: 30% of users want integrations with their existing tools, ecosystem is moat
- **How**: Event bus architecture, webhook delivery system, API documentation

**Proposal 9: Microservices Refactor (Core Service)**
- **What**: Break monolith into smaller services for scalability and velocity
- **Why**: Monolithic architecture slowing development, 30% of time spent on refactoring
- **How**: Identify service boundaries, extract [X service] first, incremental migration

### UX/Polish

**Proposal 10: Onboarding Overhaul**
- **What**: Reduce setup from 10 steps/2 hours to 3 steps/15 minutes
- **Why**: 65% drop-off during onboarding, losing potential users before they see value
- **How**: Sensible defaults, skip optional steps, interactive tutorial, sample data

**Proposal 11: Dark Mode**
- **What**: Add dark theme option for UI
- **Why**: 40% of users requesting (modern expectation), reduces eye strain
- **How**: CSS variables for theming, theme toggle in settings, respect system preference

**Proposal 12: Mobile-Responsive Design**
- **What**: Optimize UI for mobile browsers (touch targets, layout)
- **Why**: 25% of traffic is mobile, current experience broken on small screens
- **How**: Responsive CSS, touch-friendly controls, mobile navigation pattern

### Platform Expansion

**Proposal 13: Native Mobile Apps (iOS/Android)**
- **What**: Build native mobile apps for on-the-go access
- **Why**: 40% of users want mobile access, 7 feature requests, competitors offering
- **How**: React Native or Flutter for cross-platform, native API integration

**Proposal 14: Third-Party Integrations (Zapier, Slack)**
- **What**: Pre-built integrations with popular tools (Slack, Zapier, GitHub)
- **Why**: Users want product to fit into existing workflows, not replace entire stack
- **How**: Integration APIs for Zapier/Make, Slack app, GitHub Actions

**Proposal 15: Enterprise SSO (SAML, OAuth)**
- **What**: Support enterprise authentication (SAML, OAuth, SCIM provisioning)
- **Why**: Blocking 20% of enterprise deals, table stakes for enterprise sales
- **How**: SAML library integration, OAuth provider support, user provisioning API
```

---

### Step 3: Impact Assessment (15-20 min)

**Objective**: Estimate the user and business impact of each proposal

**Actions**:
1. **Reach Estimation**: How many users will benefit?
   - Count: Number of users per month/quarter
   - Percentage: % of total user base
   - Segment: Which personas benefit most?
2. **User Impact**: How much does it improve their experience?
   - Time saved (e.g., "Saves 10 min/day")
   - Friction reduced (e.g., "Reduces steps from 10 to 3")
   - Delight created (e.g., "Makes task 10x easier")
   - Use impact scale:
     - **0.25x** = Minimal (minor polish)
     - **0.5x** = Low (nice improvement)
     - **1x** = Medium (noticeable benefit)
     - **2x** = High (major improvement)
     - **3x** = Massive (transformative)
3. **Business Impact**: How does it affect key metrics?
   - Acquisition (signups, conversion rate)
   - Activation (time-to-value, aha moment rate)
   - Retention (churn reduction, engagement increase)
   - Revenue (upsells, expansion, new market)
   - Referral (word-of-mouth, NPS increase)
4. **Strategic Alignment**: Does it support business goals?
   - Competitive parity vs differentiation
   - Short-term quick win vs long-term bet
   - Core product vs platform expansion

**Output Format**:
```markdown
## Impact Assessment

| Proposal | Reach | User Impact | Business Impact | Strategic Value | Total Impact Score |
|----------|-------|-------------|-----------------|-----------------|-------------------|
| 1. Bulk Operations | 60% (600 users) | 2x (Saves 20min/day) | Retention +10%, NPS +15 | Parity (4/5 competitors have) | High |
| 2. Real-Time Collab | 40% (400 users) | 2x (Modern expectation) | Activation +20%, Retention +15% | Differentiator | Very High |
| 3. AI Suggestions | 80% (800 users) | 3x (Automates 50% work) | Retention +25%, Revenue +20% | Major differentiator | Massive |
| 4. Advanced Search | 70% (700 users) | 1x (Improves find-ability) | Engagement +10% | Parity | Medium |
| 5. Keyboard Shortcuts | 30% (300 power users) | 2x (10x faster for them) | Retention +30% for power users | Differentiator | High |
| 6. Performance Opt | 20% (200 large dataset users) | 2x (4x speed improvement) | Churn prevention (-50% for segment) | Parity | High |
| 7. API Rate Limiting | 100% (all users) | 0.5x (Prevents downtime) | Risk mitigation (uptime) | Technical necessity | Medium |
| 8. Webhooks/API | 30% (300 users) | 2x (Enables integrations) | Ecosystem moat, Revenue +15% | Strategic | High |
| 9. Microservices | 0% (no direct user impact) | 0.5x (Faster features long-term) | Dev velocity +30% | Technical investment | Low (user), High (biz) |
| 10. Onboarding Overhaul | 100% (all new users) | 3x (65% → 85% activation) | Acquisition +30%, Revenue +30% | Quick win | Massive |
| 11. Dark Mode | 40% (400 users) | 0.5x (Preference, eye strain) | NPS +5 | Polish | Low |
| 12. Mobile-Responsive | 25% (250 mobile users) | 1x (Fixes broken experience) | Retention +20% for mobile | Parity | Medium |
| 13. Native Mobile Apps | 50% (500 potential mobile users) | 2x (Native experience) | Market expansion +40% | Platform bet | High |
| 14. Integrations | 30% (300 users) | 1x (Fits into workflow) | Ecosystem, Retention +10% | Parity | Medium |
| 15. Enterprise SSO | 5% (50 enterprise users) | 1x (Required for enterprise) | Revenue +50% (enterprise deals) | Growth unlock | High |

### Detailed Impact Examples

**Proposal 3: AI-Powered Smart Suggestions**
- **Reach**: 800 users/month (80% of active users)
- **User Impact**: 3x Massive
  - Automates 50% of repetitive tasks (saves 1 hour/day for daily users)
  - Reduces cognitive load (no need to remember workflows)
  - Delights with "magic" experience
- **Business Impact**:
  - Retention: +25% (users become dependent on suggestions)
  - Revenue: +20% (higher willingness to pay for AI features)
  - Differentiation: Major moat, 0/5 competitors have this yet
- **Strategic Value**: Major differentiator, first-mover advantage in AI-powered category
- **Total**: Massive impact

**Proposal 10: Onboarding Overhaul**
- **Reach**: 1000 new users/month (100% of new users)
- **User Impact**: 3x Massive
  - Reduces time-to-first-value from 2 hours to 15 minutes (8x faster)
  - Increases activation rate from 35% to 85% (2.4x improvement)
  - Reduces confusion and frustration during critical first impression
- **Business Impact**:
  - Acquisition: +30% (more signups convert to activated users)
  - Revenue: +30% (more activated users = more paying customers)
  - Word-of-mouth: +20% (great onboarding = users tell friends)
- **Strategic Value**: Quick win, high ROI, foundational for growth
- **Total**: Massive impact
```

---

### Step 4: Effort Estimation (15-20 min)

**Objective**: Estimate development effort, complexity, and dependencies

**Actions**:
1. **Development Time**: Estimate in person-weeks or person-months
   - Break down into components (backend, frontend, testing, docs)
   - Consider: Feature complexity, code changes, new dependencies
   - Scale:
     - **0.5** = <1 week
     - **1** = 1-2 weeks
     - **2** = 2-4 weeks
     - **4** = 1-2 months
     - **8** = 2-4 months
     - **16+** = >4 months (consider breaking down)
2. **Technical Complexity**: Assess difficulty
   - **Low**: Straightforward, well-understood patterns
   - **Medium**: Some new tech or moderate complexity
   - **High**: New paradigms, many unknowns, architectural changes
3. **Dependencies**: Identify blockers or prerequisites
   - Infrastructure (e.g., "Requires WebSocket server setup")
   - Other features (e.g., "Depends on Proposal 7 completing first")
   - External (e.g., "Needs third-party API integration")
4. **Risk Factors**: Note uncertainties
   - Technical risks (unproven technology, performance concerns)
   - Scope creep risks (ill-defined requirements, many edge cases)
   - Rollout risks (breaking changes, backward compatibility)

**Output Format**:
```markdown
## Effort Estimation

| Proposal | Dev Effort | Complexity | Dependencies | Risks | Confidence |
|----------|-----------|------------|--------------|-------|------------|
| 1. Bulk Operations | 2 weeks | Medium | None | Scope creep (many edge cases) | 80% |
| 2. Real-Time Collab | 8 weeks | High | WebSocket infra | Technical (conflict resolution) | 50% |
| 3. AI Suggestions | 4 weeks | Medium | LLM API integration | Cost (API usage), accuracy | 60% |
| 4. Advanced Search | 3 weeks | Medium | Search engine (Elasticsearch?) | New infrastructure | 70% |
| 5. Keyboard Shortcuts | 1 week | Low | None | None | 90% |
| 6. Performance Opt | 4 weeks | High | Database refactor | Scope (may uncover more debt) | 60% |
| 7. API Rate Limiting | 1 week | Low | Redis/cache layer | None | 90% |
| 8. Webhooks/API | 3 weeks | Medium | Event bus architecture | Reliability (delivery guarantees) | 70% |
| 9. Microservices | 16+ weeks | Very High | Entire architecture | Massive scope, long-term project | 40% |
| 10. Onboarding Overhaul | 2 weeks | Low | None | Requires user testing | 80% |
| 11. Dark Mode | 1 week | Low | None | None | 95% |
| 12. Mobile-Responsive | 2 weeks | Low | None | None | 85% |
| 13. Native Mobile Apps | 12 weeks | High | Mobile dev expertise | Resource (need mobile devs) | 50% |
| 14. Integrations | 4 weeks | Medium | API/webhooks (Proposal 8) | Maintenance (each integration) | 70% |
| 15. Enterprise SSO | 3 weeks | Medium | SAML library | Security review, testing | 70% |

### Detailed Effort Examples

**Proposal 2: Real-Time Collaboration**
- **Development Time**: 8 weeks (2 engineers)
  - Backend: WebSocket server setup (2 weeks)
  - Frontend: Live update UI (2 weeks)
  - Conflict resolution: Operational transforms (3 weeks)
  - Testing & edge cases: (1 week)
- **Complexity**: High
  - New technology (WebSockets, OT algorithm)
  - Many edge cases (concurrent edits, offline, reconnection)
  - Performance considerations (scaling WebSocket connections)
- **Dependencies**: Requires WebSocket infrastructure (load balancer support, Redis for pub/sub)
- **Risks**:
  - Technical: Operational transforms are complex, may take longer than estimated
  - Performance: WebSocket scaling could be expensive or difficult
  - Scope creep: Users may expect more real-time features once launched
- **Confidence**: 50% (unproven technology for the team)

**Proposal 10: Onboarding Overhaul**
- **Development Time**: 2 weeks (1 engineer, 1 designer)
  - Design: New onboarding flow (0.5 weeks)
  - Frontend: Interactive tutorial UI (1 week)
  - Backend: Sample data generation (0.5 weeks)
- **Complexity**: Low
  - Mostly UI/UX changes, well-understood patterns
  - No new infrastructure or technologies
- **Dependencies**: None
- **Risks**:
  - Requires user testing to validate new flow works better
  - May need iteration based on feedback
- **Confidence**: 80% (straightforward implementation, main uncertainty is user validation)
```

---

### Step 5: Prioritization Framework (20-25 min)

**Objective**: Rank proposals using RICE scores and value-complexity matrix

**Actions**:
1. **RICE Scoring**: For each proposal, calculate:
   - **Reach**: Users impacted per quarter
   - **Impact**: User impact score (0.25, 0.5, 1, 2, 3)
   - **Confidence**: How certain are we? (50%, 80%, 100%)
   - **Effort**: Development time in person-months
   - **RICE Score** = (Reach × Impact × Confidence) / Effort
2. **ICE Scoring** (alternative, simpler):
   - **Impact**: 1-10 scale
   - **Confidence**: 1-10 scale
   - **Ease**: 1-10 scale (inverse of effort)
   - **ICE Score** = (Impact × Confidence × Ease) / 3
3. **Value-Complexity Matrix**: Plot proposals on 2x2 grid
   - **Y-axis**: Value (user + business impact)
   - **X-axis**: Complexity (effort + technical risk)
   - **Quadrants**:
     - High Value, Low Complexity = **Quick Wins** (do first)
     - High Value, High Complexity = **Strategic Bets** (plan carefully)
     - Low Value, Low Complexity = **Fill-ins** (do if time)
     - Low Value, High Complexity = **Avoid** (deprioritize)
4. **Kano Model** (optional): Categorize by user satisfaction impact
   - **Basic**: Expected, dissatisfaction if missing (e.g., security, uptime)
   - **Performance**: Linear satisfaction (e.g., faster = better)
   - **Delight**: Unexpected wow factor (e.g., AI suggestions, dark mode)

**Output Format**:
```markdown
## Prioritization Framework

### RICE Scores (Ranked)

| Rank | Proposal | Reach | Impact | Confidence | Effort | RICE Score | Category |
|------|----------|-------|--------|------------|--------|------------|----------|
| 1 | 10. Onboarding Overhaul | 3000 | 3 | 80% | 0.5 | 14400 | Quick Win |
| 2 | 5. Keyboard Shortcuts | 900 | 2 | 90% | 0.25 | 6480 | Quick Win |
| 3 | 3. AI Suggestions | 2400 | 3 | 60% | 1 | 4320 | Strategic Bet |
| 4 | 1. Bulk Operations | 1800 | 2 | 80% | 0.5 | 5760 | Quick Win |
| 5 | 6. Performance Opt | 600 | 2 | 60% | 1 | 720 | Targeted Fix |
| 6 | 15. Enterprise SSO | 150 | 1 | 70% | 0.75 | 140 | Growth Unlock |
| 7 | 2. Real-Time Collab | 1200 | 2 | 50% | 2 | 600 | Strategic Bet |
| 8 | 8. Webhooks/API | 900 | 2 | 70% | 0.75 | 1680 | Strategic |
| 9 | 4. Advanced Search | 2100 | 1 | 70% | 0.75 | 1960 | Enhancement |
| 10 | 14. Integrations | 900 | 1 | 70% | 1 | 630 | Ecosystem |
| 11 | 11. Dark Mode | 1200 | 0.5 | 95% | 0.25 | 2280 | Polish |
| 12 | 12. Mobile-Responsive | 750 | 1 | 85% | 0.5 | 1275 | Parity |
| 13 | 7. API Rate Limiting | 3000 | 0.5 | 90% | 0.25 | 5400 | Technical |
| 14 | 13. Native Mobile Apps | 1500 | 2 | 50% | 3 | 500 | Platform Bet |
| 15 | 9. Microservices | 0 | 0.5 | 40% | 4 | 0 | Tech Debt |

**RICE Calculation Example**:
- Proposal 10: (3000 reach × 3 impact × 80% confidence) / 0.5 effort = 14400

### Value-Complexity Matrix

```
High Value    |                    |
              | [Strategic Bets]   | [Quick Wins]
              | - #3 AI (4320)     | - #10 Onboard (14400)
              | - #2 Realtime (600)| - #5 Keyboard (6480)
              | - #8 Webhooks(1680)| - #1 Bulk Ops (5760)
              |                    | - #7 Rate Limit (5400)
--------------+--------------------+--------------------
              | [Avoid]            | [Fill-ins]
Low Value     | - #9 Microservices | - #11 Dark Mode (2280)
              | - #13 Mobile Apps  | - #4 Search (1960)
              |   (low confidence) | - #12 Responsive (1275)
              |                    |
         High Complexity      Low Complexity
```

### Prioritization Tiers

**Tier 1: Ship Now (Q1) - Quick Wins**
1. **Onboarding Overhaul** (RICE: 14400)
   - Rationale: Massive impact, low effort, high confidence
   - Timeline: 2 weeks
   - Expected: Activation 35% → 85%, +30% revenue

2. **Keyboard Shortcuts** (RICE: 6480)
   - Rationale: High impact for power users, very low effort
   - Timeline: 1 week
   - Expected: Power user retention +30%, NPS +20

3. **API Rate Limiting** (RICE: 5400)
   - Rationale: Technical necessity, prevents downtime risk
   - Timeline: 1 week
   - Expected: Uptime protection, enterprise requirement

4. **Bulk Operations** (RICE: 5760)
   - Rationale: High user request volume, clear ROI
   - Timeline: 2 weeks
   - Expected: Time savings, retention +10%, NPS +15

**Tier 2: Plan & Build (Q2) - Strategic Bets**
5. **AI-Powered Suggestions** (RICE: 4320)
   - Rationale: Major differentiator, first-mover advantage
   - Timeline: 4 weeks (MVP), iterate
   - Expected: Retention +25%, revenue +20%, major differentiator
   - Risk: API cost, accuracy, requires experimentation

6. **Webhooks/API** (RICE: 1680)
   - Rationale: Ecosystem moat, enables integrations
   - Timeline: 3 weeks
   - Expected: Retention +10%, ecosystem growth
   - Note: Prerequisite for Proposal 14 (Integrations)

7. **Real-Time Collaboration** (RICE: 600)
   - Rationale: Modern expectation, competitive parity
   - Timeline: 8 weeks
   - Expected: Activation +20%, retention +15%
   - Risk: High complexity, may take longer than estimated

**Tier 3: Backlog (Q3-Q4)**
8. **Advanced Search** (RICE: 1960)
9. **Dark Mode** (RICE: 2280)
10. **Mobile-Responsive Design** (RICE: 1275)
11. **Third-Party Integrations** (RICE: 630) - depends on #6

**Tier 4: Strategic Consideration (6-12 months)**
12. **Enterprise SSO** (RICE: 140) - Low user volume today but revenue unlock for enterprise
13. **Performance Optimization** (RICE: 720) - Targeted to specific user segment with pain
14. **Native Mobile Apps** (RICE: 500) - Major investment, validate demand first

**Deprioritized (Not Now)**
15. **Microservices Refactor** (RICE: 0) - No direct user value, long-term tech investment
    - Revisit when dev velocity becomes critical bottleneck (6-12 months)

### Kano Model Classification

**Basic (Must-Have - Dissatisfiers if missing)**:
- API Rate Limiting (#7)
- Enterprise SSO (#15) - for enterprise segment
- Performance Optimization (#6) - for large dataset users

**Performance (Linear Satisfaction)**:
- Bulk Operations (#1)
- Advanced Search (#4)
- Integrations (#14)

**Delight (Surprise & Wow)**:
- AI Suggestions (#3)
- Keyboard Shortcuts (#5)
- Dark Mode (#11)
```

---

### Step 6: Proposal Documentation (20-25 min)

**Objective**: Create detailed business cases for top 5-10 proposals

**Actions**:
1. **Proposal Template**: For each top proposal, document:
   - **Executive Summary**: 2-3 sentence overview
   - **Problem Statement**: User pain point or opportunity
   - **Proposed Solution**: What we'll build and how
   - **Success Metrics**: How we'll measure success
   - **Target Personas**: Who benefits most
   - **Impact Analysis**: User and business impact (detailed)
   - **Effort Estimate**: Time, resources, dependencies
   - **Implementation Plan**: High-level approach and milestones
   - **Risks & Mitigations**: What could go wrong and how to address
   - **Go/No-Go Recommendation**: Recommended decision with rationale
2. **Visual Aids**: Include diagrams, mockups, or examples where helpful
3. **Supporting Data**: Link to evidence (user requests, competitive research, analytics)

**Output Format**:
```markdown
## Top Improvement Proposals (Detailed)

---

### Proposal 1: Onboarding Overhaul
**RICE Score: 14400 | Priority: P0 (Ship in Q1)**

#### Executive Summary
Redesign onboarding flow to reduce time-to-first-value from 2 hours to 15 minutes and increase activation rate from 35% to 85%. This is a high-impact, low-effort improvement that directly addresses our largest growth bottleneck.

#### Problem Statement
**User Pain Point**: New users face a 10-step setup process that takes 2 hours on average. 65% of users abandon during onboarding, never experiencing the product's core value.

**Evidence**:
- Activation rate: 35% (industry avg: 60-70%)
- Time-to-first-value: 2 hours (competitors: 15-30 min)
- User feedback: "Too complicated", "Gave up halfway", "Didn't know what to do"
- Drop-off points: Step 3 (configuration, 30% drop), Step 7 (integration, 20% drop)

**Business Impact**: We're losing 650 potential users per month (65% of 1000 signups), equivalent to $130K/month in potential revenue.

#### Proposed Solution
**What**: Redesign onboarding with sensible defaults, optional steps, interactive tutorial, and sample data.

**How**:
1. **Reduce required steps**: 10 → 3 (create account, choose template, see core feature)
2. **Sensible defaults**: Auto-configure 80% use case, allow customization later
3. **Skip optional steps**: Allow "Skip for now" on integrations, advanced settings
4. **Interactive tutorial**: Guide users through core workflow with sample data
5. **Templates & examples**: Pre-populate with realistic sample data for instant value

**Inspiration**: Similar to [Competitor X]'s onboarding, Notion's template gallery, Stripe's test mode

#### Success Metrics
**Primary**:
- Activation rate: 35% → 85% (target: 60%+ signups complete onboarding)
- Time-to-first-value: 2 hours → 15 minutes

**Secondary**:
- Week 1 retention: 40% → 70%
- NPS score: +20 points (from "frustrated by setup" feedback reduction)
- Support tickets: -50% (onboarding-related questions)

**Leading Indicators** (track weekly):
- % of users completing step 1, 2, 3
- Average time spent in onboarding
- Drop-off rate at each step

#### Target Personas
- **Primary**: Startup Steve (solo founders, need to move fast)
- **Primary**: Developer Dan (wants to start coding, not configuring)
- **Secondary**: Manager Maria (wants quick team onboarding)

#### Impact Analysis

**User Impact**: 3x Massive
- Reduces friction from "overwhelming" to "delightful"
- Emotional: Confidence ("I understand this"), productivity ("I'm making progress")
- Social: More likely to recommend to peers (less embarrassment about complexity)

**Business Impact**:
- **Acquisition**: +30% effective signups (650 more activated users/month)
- **Revenue**: +$130K/month from activated users converting to paid
- **Word-of-mouth**: +20% referrals (great onboarding = users tell friends)
- **Support costs**: -$10K/month (fewer onboarding support tickets)

**Strategic Value**:
- Quick win with massive ROI (2 weeks effort → $1.56M annual revenue)
- Foundational for growth (can't scale marketing if onboarding is broken)
- Competitive advantage (vs complex competitors like [Competitor 1])

#### Effort Estimate
**Development Time**: 2 weeks (1 engineer, 1 designer)
- Design new flow: 0.5 weeks
- Build interactive tutorial UI: 1 week
- Sample data generation: 0.5 weeks

**Resources**:
- 1 frontend engineer
- 1 product designer
- PM time (10 hours: spec, user testing, launch)

**Dependencies**: None

**Complexity**: Low (UI/UX changes, no new infrastructure)

#### Implementation Plan

**Week 1: Design & Prototype**
- Days 1-2: Analyze current drop-off points in detail (analytics, user interviews)
- Days 3-4: Design new onboarding flow (wireframes, prototypes)
- Day 5: User testing with 5 users (validate new flow reduces friction)

**Week 2: Build & Launch**
- Days 1-3: Implement new onboarding UI
- Day 4: QA testing (cross-browser, edge cases)
- Day 5: Soft launch to 10% of users, monitor metrics

**Week 3: Iterate & Scale**
- Days 1-2: Analyze data from 10% cohort
- Days 3-4: Address any issues or confusion points
- Day 5: Roll out to 100% of users

**Post-Launch**:
- Weekly: Monitor activation rate, time-to-value, drop-off points
- Monthly: User interviews to gather qualitative feedback
- Iterate: Continuously improve based on data

#### Risks & Mitigations

**Risk 1: New flow doesn't improve activation**
- Likelihood: Low (validated with user testing)
- Impact: Medium (wasted 2 weeks)
- Mitigation: User test prototypes before building, soft launch to 10% first
- Rollback: Keep old onboarding code, can revert if metrics degrade

**Risk 2: Sample data confuses users**
- Likelihood: Medium (users may not realize it's sample data)
- Impact: Low (minor confusion)
- Mitigation: Clear labels "Sample data - Replace with your own", easy "Clear all" button

**Risk 3: "Skip for now" causes users to miss important steps**
- Likelihood: Medium
- Impact: Medium (users may not set up critical features)
- Mitigation: Contextual prompts later ("You skipped X, here's why it matters"), analytics to track skip rates

#### Go/No-Go Recommendation
**✅ GO - Strongly Recommend**

**Rationale**:
- **Massive impact**: Doubles activation rate, $1.56M annual revenue potential
- **Low effort**: 2 weeks, no technical complexity
- **High confidence**: 80% - validated with user research, clear problem
- **Strategic fit**: Addresses #1 growth bottleneck, foundational for scaling
- **Quick win**: Ship in Q1, see results immediately

**Decision**: Prioritize as P0 (highest priority), start immediately.

---

### Proposal 2: Keyboard Shortcuts & Command Palette
**RICE Score: 6480 | Priority: P0 (Ship in Q1)**

#### Executive Summary
Add Cmd+K command palette and common keyboard shortcuts to enable power users to navigate 10x faster, improving retention for high-value users and differentiating from mouse-heavy competitors.

#### Problem Statement
**User Pain Point**: Power users (30% of user base, 70% of usage) want faster navigation. Current mouse-only interface slows their workflow.

**Evidence**:
- 15+ user requests for keyboard shortcuts (Issues #234, #567, etc.)
- User feedback: "Wish I could do everything with keyboard", "Too slow clicking through menus"
- Competitors: 3/5 competitors offer keyboard shortcuts, seen as modern expectation
- Power users average 50 actions/day, could be 150+ with keyboard efficiency

**Business Impact**: Power users have 2x higher LTV ($500 vs $250 avg). Improving their experience increases retention and word-of-mouth.

#### Proposed Solution
**What**: Implement Cmd+K command palette and common keyboard shortcuts for navigation and actions.

**How**:
1. **Command Palette** (Cmd+K): Searchable list of all actions, fuzzy search
2. **Navigation Shortcuts**: Cmd+1/2/3 for sections, Cmd+/ for search, Cmd+N for new item
3. **Action Shortcuts**: Cmd+S for save, Cmd+E for edit, Cmd+D for delete, etc.
4. **Help Menu**: Cmd+? to show all shortcuts, tooltips for discoverability

**Inspiration**: VSCode command palette, Linear keyboard-first UX, Superhuman email

#### Success Metrics
**Primary**:
- Power user retention: 85% → 95% (define power users as 10+ actions/day)
- Actions per user: 50/day → 100/day for power users

**Secondary**:
- NPS from power users: +25 points
- Shortcut usage: 50% of power users using shortcuts within 2 weeks
- User feedback: Positive mentions of "fast", "efficient", "keyboard" in surveys

#### Target Personas
- **Primary**: Developer Dan (wants CLI-like efficiency)
- **Secondary**: Manager Maria (navigates product daily, appreciates speed)

#### Impact Analysis
**User Impact**: 2x High (for 30% of users)
- Saves 5-10 minutes per day for power users
- Emotional: Feel productive and in control
- Social: Power users become evangelists ("fastest tool in the category")

**Business Impact**:
- Retention: +10% overall (+30% for power user segment)
- Revenue: Power users have 2x LTV, retaining them = +$50K annual revenue
- Differentiation: Keyboard-first UX vs mouse-heavy competitors

**Effort**: 1 week (low complexity)

#### Implementation Plan
**Week 1**: Design shortcuts, build command palette, QA, launch
- Use library like `cmdk` for command palette
- Map shortcuts to existing actions
- Add help menu and tooltips

#### Risks & Mitigations
**Risk**: Conflicts with browser shortcuts
- Mitigation: Follow standard conventions (Cmd+K, Cmd+N), allow customization

#### Go/No-Go Recommendation
**✅ GO - Strongly Recommend**
- High impact for high-value users, low effort, clear differentiator

---

### Proposal 3: AI-Powered Smart Suggestions
**RICE Score: 4320 | Priority: P1 (Plan & Build in Q2)**

#### Executive Summary
Integrate AI/LLM to automatically suggest next actions based on user behavior patterns, reducing manual work by 50% and creating a major competitive differentiator.

#### Problem Statement
**User Pain Point**: Users repeat common workflows manually. AI could predict and automate 50% of repetitive tasks.

**Evidence**:
- Workflow analysis: 60% of actions are repetitive (create → tag → assign → notify)
- User feedback: "Wish it could do this automatically", "Same thing every time"
- Market trend: AI-powered tools growing 50% YoY, user expectation shifting
- Competitors: 0/5 competitors offer AI suggestions yet (first-mover opportunity)

#### Proposed Solution
**What**: LLM integration that learns user patterns and suggests next actions.

**How**:
1. Track user action sequences (with consent)
2. Identify patterns (e.g., "When user creates [X], they usually [Y]")
3. Surface suggestions: "Would you like to [Y]?" with one-click accept
4. Continuously learn and improve accuracy

**Examples**:
- "You usually tag new items with 'urgent' - add it now?"
- "You typically assign [task type] to [person] - assign?"
- "Based on similar items, you might want to [action]"

#### Success Metrics
**Primary**:
- Time saved: 50% reduction in repetitive actions (measure: actions per task)
- Feature adoption: 70% of users accept at least one suggestion per week

**Secondary**:
- Retention: +25% (users become dependent on suggestions)
- Revenue: +20% (willingness to pay premium for AI features)
- NPS: +30 (from "magic" experience)

#### Impact Analysis
**User Impact**: 3x Massive
- Automates 50% of manual work (saves 30-60 min/day for daily users)
- Emotional: Delight (feels like magic), productivity (less tedious work)
- Social: Early adopters feel like insiders using cutting-edge features

**Business Impact**:
- Retention: +25% (AI suggestions become habit-forming)
- Revenue: +20% ($200K annual revenue increase)
- Differentiation: Major moat, 0/5 competitors have this (first-mover)
- PR value: "AI-powered [category]" positioning, media attention

**Effort**: 4 weeks (MVP), then iterate

#### Implementation Plan
**Weeks 1-2: MVP**
- Integrate LLM API (OpenAI, Anthropic)
- Build pattern detection (simple heuristics first)
- Add suggestion UI (toast notification, accept/dismiss)

**Weeks 3-4: Refinement**
- Track suggestion acceptance rate
- Improve accuracy based on feedback
- Add more suggestion types

**Ongoing**:
- Monitor API costs (set budget caps)
- Continuously improve suggestions based on user feedback
- A/B test different suggestion types

#### Risks & Mitigations
**Risk 1: API costs too high**
- Mitigation: Set budget caps, cache common queries, use smaller models for simple suggestions
- Estimated cost: $0.01-0.05 per user per month (affordable at scale)

**Risk 2: Suggestions inaccurate, annoy users**
- Mitigation: Start with high-confidence suggestions only (80%+ certainty)
- Allow users to dismiss or turn off suggestions
- Track acceptance rate, improve over time

**Risk 3: Privacy concerns (learning from user data)**
- Mitigation: Clearly communicate data usage, allow opt-out
- Keep data anonymous, use patterns not individual actions
- Compliance with GDPR, CCPA

#### Go/No-Go Recommendation
**✅ GO - Recommend (with caveats)**
- Massive impact potential, major differentiator
- Moderate effort (4 weeks MVP)
- Risks manageable with careful implementation
- Recommend: Build MVP in Q2, iterate based on feedback, scale if successful

---

### Proposal 4: Bulk Operations
**RICE Score: 5760 | Priority: P0 (Ship in Q1)**

[Similar detailed format...]

---

### Proposal 5: Real-Time Collaboration
**RICE Score: 600 | Priority: P1 (Plan & Build in Q2)**

[Similar detailed format...]

---

[Continue for top 5-10 proposals...]
```

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **Opportunity mining**: Researched technical debt, feature requests, UX friction, competitive gaps, innovation opportunities
- [ ] **Proposal generation**: Created 10-15 specific, focused proposals across categories
- [ ] **Impact assessment**: Estimated reach, user impact, business impact for each proposal
- [ ] **Effort estimation**: Estimated development time, complexity, dependencies, risks
- [ ] **Prioritization**: Calculated RICE scores, plotted value-complexity matrix, categorized by tier
- [ ] **Detailed proposals**: Documented top 5-10 proposals with business cases, success metrics, implementation plans
- [ ] **Evidence-based**: All estimates grounded in user feedback, competitive research, or data
- [ ] **Actionable**: Clear go/no-go recommendations with rationale
- [ ] **Formatted clearly**: Tables, headings, examples for easy scanning

---

## Tips for Effective Improvement Proposals

1. **Start with evidence, not opinions**: Ground every proposal in user feedback, data, or competitive analysis
2. **Be specific**: "Improve onboarding" is vague; "Reduce onboarding from 10 steps to 3" is actionable
3. **Think in bets**: Some proposals are high-confidence (quick wins), others are experiments (strategic bets)
4. **Balance short and long term**: Mix quick wins (1-2 weeks) with strategic investments (months)
5. **Consider sequencing**: Some proposals unlock others (webhooks enable integrations)
6. **Estimate conservatively**: Add 20% buffer to effort estimates
7. **Define success metrics upfront**: How will you know if the proposal succeeded?
8. **Show trade-offs**: Acknowledge risks and alternatives, don't oversell
9. **Prioritize ruthlessly**: Not everything can be P0; focus on top 3-5
10. **Update regularly**: Priorities shift as product and market evolve; refresh quarterly

---

## Integration with Other Skills

This skill works well with:

- **product-evolution-analysis**: Use opportunities from evolution analysis to seed proposals
- **competitive-intelligence**: Identify feature gaps to close or differentiation opportunities
- **persona-definition**: Prioritize proposals based on persona needs and impact
- **changelog-creation**: Communicate shipped proposals to users through compelling changelogs

---

*Use this skill whenever you need to generate, prioritize, and build business cases for product improvements and new features.*
