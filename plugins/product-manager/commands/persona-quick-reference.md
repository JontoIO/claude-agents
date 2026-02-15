# Persona Quick Reference Command

Generates a basic persona profile in 5 minutes for quick reference during product decisions, without conducting full persona research.

## Purpose

Create a quick persona when:
- Need to ground feature discussions in user context
- Evaluating if a feature fits target users
- Making fast prioritization decisions
- Onboarding new team members to user base
- Quick sanity check during design/planning

## When to Use

**Use persona-quick-reference when**:
- Need persona in 5 minutes
- Working with existing user data/knowledge
- Quick reference for decision-making
- Validating assumptions rapidly
- Teaching team about users

**Use full persona-definition skill when**:
- Creating official persona documentation
- Need research-backed personas
- Building comprehensive user profiles
- Strategic planning and positioning
- Presenting to stakeholders or executives

## Command Format

```bash
/persona-quick-reference [user type or segment]
```

### Optional Parameters

Add context to improve persona accuracy:

```
--based-on [source]      Data source: "analytics", "support-tickets", "surveys", "interviews"
--focus [aspect]         What to emphasize: "goals", "pain-points", "tech-savvy", "budget"
--product [name]         Your product context
--industry [type]        Industry context (B2B, B2C, SaaS, etc.)
```

## Examples

### Example 1: Basic User Persona

```bash
/persona-quick-reference Startup founder using project management tool
```

**Expected Output**:
```
# Persona Quick Reference: Startup Founder

## Core Profile
**Name**: Sam (Startup Sam)
**Age**: 28-38
**Role**: Founder/CEO, 2-10 person startup
**Industry**: Tech/SaaS
**Location**: Urban, often remote-first company

## Goals & Motivations
🎯 Primary Goals:
- Ship products fast with limited resources
- Keep team aligned without bureaucracy
- Make data-driven decisions quickly
- Scale processes as company grows

💡 What drives decisions:
- Speed > perfection
- Flexibility > enterprise features
- Learning curve matters (no time for training)
- Cost-conscious but will pay for value

## Pain Points
😤 Current Frustrations:
- Too many tools, context-switching kills productivity
- Enterprise tools are overkill and expensive
- Simple tools lack features as team grows
- Can't afford dedicated project manager

⚠️ Fears & Concerns:
- Wasting time on wrong features
- Team working on wrong priorities
- Losing momentum to tool setup/admin
- Vendor lock-in or costly migrations later

## Behavior & Habits
⏰ Daily Routine:
- Checks project status first thing (7-8am)
- Jumps between builder and manager mode
- Quick check-ins with team throughout day
- Reviews metrics/progress end of day

💻 Tech Usage:
- Tech-savvy, learns tools quickly
- Mobile-first for communication
- Uses 5-10 SaaS tools daily
- Values integrations highly (Slack, GitHub, etc.)

📱 Devices:
- Primary: MacBook
- Secondary: iPhone for quick updates
- Rarely uses tablet

## Decision-Making
✅ Says YES to features that:
- Save time immediately
- Reduce tool count (consolidation)
- Help team self-serve
- Scale with company growth
- Integrate with existing stack

❌ Says NO to features that:
- Require training/onboarding time
- Add complexity without clear ROI
- Lock them into specific workflow
- Price jumps at scale
- Need dedicated admin

## Buying Behavior
💰 Budget: $0-500/month for team tools
🔍 Research: Reads reviews, asks founder network
⏱️ Decision time: 1-2 weeks (fast)
🧪 Trial: Expects free trial, onboards quickly
💳 Payment: Credit card (not procurement)

## How They Describe Problems
"I need to see what everyone's working on without bugging them"
"Our Trello boards got out of hand, we need something more structured"
"I'm spending 2 hours a day in status meetings"
"I don't know if we're shipping the right things"

## Feature Prioritization
### Must-Have:
- Works out of the box (minimal setup)
- Mobile app (check status anywhere)
- Slack integration
- Simple permissions (admin vs member)

### Nice-to-Have:
- Templates for common workflows
- Time tracking
- Custom fields
- Reporting/analytics

### Don't Care:
- Gantt charts
- Resource management
- Advanced time tracking
- Enterprise SSO (yet)

## Persona Confidence: Medium
- ✓ Based on common startup founder patterns
- ✓ Validated by typical SaaS usage data
- ⚠ Not research-backed for your specific product
- ⚠ Generalizes across industries

**Use this for**: Quick feature validation, team discussions
**Don't use this for**: Marketing copy, strategic positioning

Time to generate: 5 minutes
For research-backed persona: Use /persona-definition skill
```

### Example 2: With Data Source

```bash
/persona-quick-reference Enterprise IT buyer --based-on interviews --focus budget
```

**Expected Output**:
```
# Persona Quick Reference: Enterprise IT Buyer

## Core Profile
**Name**: Chris (Cautious Chris)
**Age**: 35-50
**Role**: IT Director / VP of IT
**Company Size**: 500-5,000 employees
**Industry**: Various (B2B focus)
**Location**: Global, corporate environment

## Goals & Motivations
🎯 Primary Goals:
- Reduce IT support burden
- Improve security and compliance
- Standardize tooling across organization
- Demonstrate ROI to C-suite

💡 What drives decisions:
- Risk mitigation > innovation
- Vendor reliability > cutting-edge features
- Security & compliance are non-negotiable
- Long-term total cost of ownership

## Pain Points (Budget-Focused)
😤 Current Frustrations:
- Budget scrutiny has increased
- Shadow IT purchases bypass them
- Vendors nickel-and-dime for features
- Hard to predict annual costs
- Unexpected pricing at renewal

⚠️ Budget-Specific Concerns:
- Surprise bills from usage-based pricing
- Getting budget approval takes 3-6 months
- CFO questions all new software spend
- Need to show cost savings/avoidance
- Per-user pricing scales painfully

## Behavior & Habits
⏰ Decision Timeline:
- 3-6 month evaluation cycle
- Quarterly budget review
- Annual contract negotiations
- Multi-stakeholder approval needed

💻 Procurement Process:
- RFP or vendor comparison matrix
- Security/compliance questionnaire
- Legal review of contracts
- References from similar companies
- Proof of concept with IT team

## Decision-Making (Budget Lens)
✅ Says YES to pricing that:
- Predictable, flat annual fee
- Volume discounts clearly defined
- Multi-year commit discounts (15-20%)
- Includes support in base price
- Transparent upgrade paths

❌ Says NO to pricing that:
- Surprise overages or hidden fees
- Per-user scales poorly (100+ users)
- Requires usage estimation
- Frequent price increases
- Separate charge for support

## Buying Behavior
💰 Budget: $50K - $500K annual contract
🔍 Research: Gartner, peer recommendations, case studies
⏱️ Decision time: 3-6 months (procurement cycle)
🧪 Trial: Requires POC with IT team (30-60 days)
💳 Payment: Invoice, purchase order, procurement

## Budget Approval Requirements
📊 Must demonstrate:
- ROI calculation (hard savings)
- Payback period <18 months
- Cost comparison to alternatives
- Total cost of ownership
- Risk if not purchased

📝 Decision packet includes:
- Executive summary (1 page)
- Cost-benefit analysis
- Security/compliance validation
- References from similar companies
- Implementation timeline

## How They Describe Problems
"We're spending too much on duplicate tools"
"I need predictable costs for annual planning"
"Can't get budget approved without clear ROI"
"Every vendor wants to charge per user, it's unsustainable"
"Need to consolidate vendors to reduce overhead"

## Pricing Preferences
### Preferred Model:
1. Flat annual fee (unlimited users)
2. Tiered pricing (clear breakpoints)
3. Site license
4. Usage-based with caps

### Rejected Models:
- Pure per-user (scales poorly)
- Pay-as-you-go (unpredictable)
- Feature paywalls (nickel-and-dime)
- Frequent price increases

## Budget Red Flags
🚩 Deal breakers:
- No enterprise pricing tier
- Can't lock in multi-year rate
- Support costs extra
- No volume discounts at scale
- Opaque pricing (call for quote)

## Feature Prioritization
### Must-Have:
- Enterprise SSO (SAML)
- Admin controls and audit logs
- SOC 2 / ISO certifications
- SLA guarantees (99.9%+)
- Dedicated support contact

### Nice-to-Have:
- Advanced analytics
- Custom branding
- API access
- Training/onboarding

### Don't Care About:
- Cutting-edge features (risk)
- Consumer-focused UI polish
- Frequent updates (prefer stability)

## Persona Confidence: Medium-High
- ✓ Based on interview patterns
- ✓ Budget focus aligned with common concerns
- ⚠ Industry-specific nuances may vary
- ⚠ Company size affects priorities

**Use this for**: Pricing discussions, enterprise sales prep
**Don't use this for**: Final pricing strategy, marketing messaging

Time to generate: 5 minutes
For research-backed persona: Use /persona-definition skill
```

### Example 3: B2C Consumer

```bash
/persona-quick-reference Fitness app user --product health-tracking --focus goals
```

**Expected Output**:
```
# Persona Quick Reference: Fitness App User

## Core Profile
**Name**: Alex (Active Alex)
**Age**: 25-40
**Occupation**: Professional (desk job)
**Fitness Level**: Beginner to Intermediate
**Location**: Urban/Suburban
**Income**: $50K-$100K

## Goals & Motivations (Primary Focus)
🎯 Fitness Goals:
- Lose 10-30 pounds
- Build consistent exercise habit
- Improve energy levels
- Look better / feel more confident

🎯 App-Specific Goals:
- Track progress visually
- Get motivation to stick with it
- Understand if effort is working
- Find workouts that fit schedule

💡 What motivates them:
- Visual progress (charts, photos)
- Streaks and milestones
- Community support / accountability
- Small wins celebrated
- Before/after transformations

💡 Why they might quit:
- Not seeing results fast enough (2-4 weeks)
- App feels like homework
- Too complicated or time-consuming
- Guilt from missing days
- Plateau in progress

## Pain Points
😤 Current Frustrations:
- Started and quit many times before
- Hard to find time (work, family, social)
- Don't know if doing it "right"
- Gym intimidating or inconvenient
- Expensive trainers/classes

⚠️ Fears & Concerns:
- Another failed attempt
- Wasting money on app subscription
- Looking foolish or judged
- Injury from incorrect form
- Results take too long

## Behavior & Habits
⏰ Daily Routine:
- Wakes up 6-7am (exercise before work ideal)
- Desk job 9-6pm
- Checks phone constantly throughout day
- Evening window (7-9pm) for workouts
- Weekends more flexible

💪 Workout Patterns:
- Prefers 20-30 min sessions (max)
- Home workouts >>> gym (convenience)
- 3-4 days/week realistic
- Cardio + some strength training
- Watches workout videos (YouTube, apps)

📱 App Usage:
- Checks app daily (morning motivation)
- Logs workouts immediately after
- Reviews weekly progress (Sunday ritual)
- Browses workout library when bored
- Shares milestones on social media

## Decision-Making (Goal-Focused)
✅ Says YES to features that:
- Show progress visually (graphs, photos)
- Celebrate milestones and streaks
- Suggest workouts (decision fatigue)
- Quick input (log in seconds)
- Motivational reminders (not pushy)

❌ Says NO to features that:
- Require complex tracking (macros, etc.)
- Too many notifications
- Shame or guilt for missing days
- Require gym equipment
- Time-consuming data entry

## How They Describe Problems
"I never stick with fitness apps more than a month"
"I don't know if my workouts are actually working"
"I need something that fits in 20 minutes"
"I lose motivation when I don't see results"
"Every app is so complicated"

## Feature Prioritization
### Must-Have (Goal-Enabling):
- Progress photos (side-by-side)
- Weight/measurement tracking with graphs
- Workout streak counter
- Quick-log workouts (tap tap done)
- Beginner-friendly routines

### Nice-to-Have:
- Social features (friends, challenges)
- Meal suggestions (not full tracking)
- Rest day guidance
- Achievement badges
- Apple Health / Google Fit sync

### Don't Care:
- Advanced metrics (VO2 max, etc.)
- Detailed macro tracking
- Exercise library (100s of exercises)
- Training plans (prefer flexibility)

## Motivation Triggers
✅ Keep them engaged:
- "You've logged 3 days this week! 🔥"
- "You're down 2 lbs this month! 📉"
- "7 day streak! Keep it up! ⭐"
- Before/after photo comparison
- "You've burned 1,200 calories this week! 💪"

❌ Push them away:
- "You missed your workout yesterday"
- "You should have logged by now"
- Constant upsells to premium
- Complicated onboarding
- Too many notifications

## Buying Behavior
💰 Budget: $5-15/month willing to pay
🔍 Research: App Store reviews, social media
⏱️ Decision time: Instant (download and try)
🧪 Trial: Expects free trial (7 days minimum)
💳 Payment: Monthly subscription (hesitant on annual)

## Subscription Conversion
✅ Will upgrade if:
- Free trial showed clear value
- Saw progress in first 2 weeks
- Need features locked behind paywall
- Price feels fair (<$15/month)
- Easy to cancel anytime

## Persona Confidence: Medium
- ✓ Based on common fitness app user patterns
- ✓ Goal-focused as requested
- ⚠ Not specific to your exact product
- ⚠ Motivation factors vary individually

**Use this for**: Feature prioritization, onboarding design
**Don't use this for**: Marketing campaigns, detailed UX research

Time to generate: 5 minutes
For research-backed persona: Use /persona-definition skill
```

### Example 4: Technical User

```bash
/persona-quick-reference Backend developer using API documentation tool --focus tech-savvy
```

**Expected Output**:
```
# Persona Quick Reference: Backend Developer (API Doc User)

## Core Profile
**Name**: Dev (Developer Dev)
**Age**: 24-38
**Role**: Backend / Full-stack Developer
**Experience**: 3-8 years professional
**Company Size**: Varies (startup to enterprise)
**Location**: Global, often remote

## Tech Savvy Profile (Primary Focus)
💻 Technical Expertise:
- Strong: Backend languages (Python, Node, Go, Java)
- Strong: REST/GraphQL API design
- Medium: Frontend frameworks (React, Vue)
- Medium: DevOps/cloud (AWS, Docker)
- Weak: Design/UX (not their focus)

🛠️ Daily Tools:
- IDE: VS Code, IntelliJ, or Vim
- Terminal: Lives in it (zsh, iTerm)
- Git: Command line, not GUI
- Postman/Insomnia for API testing
- Slack/Discord for team chat
- Notion/Markdown for notes

⚡ Technical Preferences:
- CLI > GUI when possible
- Keyboard shortcuts expert
- Markdown for documentation
- Dark mode always
- Minimal, functional UI over "pretty"

## Goals & Motivations
🎯 Primary Goals:
- Understand API quickly to implement
- Copy-paste code examples that work
- Debug issues when integration fails
- Reference docs without context-switching
- Ship feature and move to next task

💡 What drives decisions:
- Speed over perfection (deadlines loom)
- Working code examples > theory
- Good search beats good navigation
- Complete reference beats tutorials
- Up-to-date docs are critical

## Pain Points
😤 Current Frustrations:
- Docs are outdated (months old)
- Examples don't match current API version
- No code samples in their language
- Have to click 10 times to find endpoint
- Unclear error messages
- Missing authentication examples

⚠️ Technical Pet Peeves:
- Marketing fluff in docs
- Auto-playing videos
- Slow doc site (want instant)
- No syntax highlighting
- Can't copy code easily
- Docs require login

## Behavior & Habits
⏰ Doc Usage Pattern:
- Lands on docs from Google search
- Ctrl+F to find specific method/endpoint
- Copies example, pastes in code
- Tries it, fails, returns to docs
- Debugs using error messages
- Checks GitHub issues if stuck

🔍 Search Behavior:
- Google: "[API name] [endpoint] example"
- Expects exact docs page as top result
- Skips intro/getting-started pages
- Goes straight to API reference
- Uses site search if Google fails

📱 Devices:
- Primary: Laptop (Mac or Linux)
- Always: Multiple monitors
- Rarely: Mobile (docs on phone = pain)

## Decision-Making (Tech-Savvy Lens)
✅ Says YES to docs that:
- Fast search (instant results)
- Code examples in multiple languages
- Copy button for code blocks
- Dark mode
- API playground (try it live)
- curl examples
- OpenAPI/Swagger spec available

❌ Says NO to docs that:
- Slow loading (>2 seconds)
- Marketing content mixed in
- No code examples
- Outdated (wrong version)
- Video tutorials (want text)
- Require account to view

## How They Describe Problems
"Where's the f***ing authentication docs?"
"These examples are for v1, we're on v3"
"Just give me a curl example"
"Why is this so slow?"
"I can't find [specific endpoint]"
"This error message tells me nothing"

## Feature Prioritization
### Must-Have (Tech-Savvy Essentials):
- Fast search with typo tolerance
- Syntax-highlighted code blocks
- Copy button on every code example
- Version selector (v2, v3, etc.)
- API reference (all endpoints)
- Error code reference

### Nice-to-Have:
- Dark mode toggle
- API playground
- Postman collection export
- SDKs/client libraries
- Changelog with migration guide
- Community/forum link

### Don't Need:
- Video tutorials (prefer text)
- Guided tours / tooltips
- Elaborate design
- Marketing content
- Blog posts in docs

## Technical Expectations
### Code Examples:
```
✅ Good example:
curl -X POST https://api.example.com/v2/users \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "name": "John"}'

❌ Bad example:
"Send a POST request to create a user"
```

### Error Documentation:
```
✅ Good:
Error 401: Invalid token
- Check that token hasn't expired (24hr TTL)
- Verify token format: "Bearer [token]"
- Generate new token: POST /auth/token

❌ Bad:
Error 401: Unauthorized
```

## Technical Setup
🔧 Comfort Level:
- ✅ REST APIs: Expert
- ✅ JSON/XML: Expert
- ✅ OAuth 2.0: Proficient
- ✅ Webhooks: Proficient
- ⚠️ GraphQL: Learning
- ⚠️ gRPC: Interested but not used

🚀 Integration Speed:
- Simple API: 1-2 hours
- Complex API: 1-2 days
- Good docs: 50% time savings
- Bad docs: 3x longer + frustration

## Persona Confidence: Medium-High
- ✓ Based on developer behavior patterns
- ✓ Tech-savvy focus accurate for audience
- ⚠ Language preferences may vary
- ⚠ Experience level affects priorities

**Use this for**: Documentation design, feature prioritization
**Don't use this for**: Marketing messaging, sales collateral

Time to generate: 5 minutes
For research-backed persona: Use /persona-definition skill
```

## Generation Methodology

The command uses rapid profiling:

### Data Sources (Priority Order)

```
1. Existing user research (if available)
2. Product analytics patterns
3. Support ticket themes
4. User interview quotes
5. Industry standard personas
6. Comparable product users
```

### Profile Structure

```
Always includes:
- Demographics (age, role, context)
- Goals & motivations
- Pain points & fears
- Behavior & habits
- Decision-making criteria
- Feature prioritization

Optionally emphasizes (via --focus):
- Goals: Deep dive on user objectives
- Pain-points: Detailed frustrations
- Tech-savvy: Technical proficiency
- Budget: Financial constraints
```

### Confidence Scoring

```
High: Based on actual user research/data
Medium: Industry patterns + some data
Low: Assumptions + generalization
```

## Output Format

Every quick persona includes:

1. **Core Profile**
   - Demographics and context
   - Role and environment

2. **Goals & Motivations**
   - What they want to achieve
   - What drives decisions

3. **Pain Points**
   - Current frustrations
   - Fears and concerns

4. **Behavior & Habits**
   - Daily routines
   - Tool usage patterns
   - Decision timeline

5. **Feature Prioritization**
   - Must-have vs nice-to-have
   - What they ignore

6. **Confidence Level**
   - Data sources used
   - Appropriate use cases
   - When to upgrade to full skill

## Limitations

**Quick persona is NOT suitable for**:
- Official persona documentation
- Marketing strategy
- Board/investor presentations
- UX research studies
- Long-term product strategy

**Accuracy factors**:
- Generalized across users
- Not research-validated
- Best for directional guidance
- May miss nuances
- Assumes typical patterns

## Improving Persona Quality

To get more accurate personas:

1. **Specify data source**: --based-on surveys/interviews/analytics
2. **Add product context**: --product [your-product-name]
3. **Focus on what matters**: --focus goals/pain-points/budget
4. **Use real user quotes**: If you have them, share them
5. **Upgrade to full skill**: When accuracy matters

## Common Use Cases

### Feature Validation
```bash
/persona-quick-reference [target user]
# Quick sanity check: Would they use this feature?
```

### Prioritization Discussion
```bash
/persona-quick-reference [user segment]
# Ground roadmap discussion in user needs
```

### Team Alignment
```bash
/persona-quick-reference [primary user]
# Get team on same page about who we're building for
```

### Design Review
```bash
/persona-quick-reference [user type] --focus goals
# Evaluate if design serves user goals
```

### Onboarding
```bash
/persona-quick-reference [user segment]
# Quick intro for new team members
```

## Tips for Better Personas

1. **Be specific**: "Marketing manager" > "business user"

2. **Add context**: Include your product type for better fit

3. **Use focus**: Emphasize aspect relevant to current decision

4. **Validate with team**: Do these ring true?

5. **Update with data**: Refine as you learn more

6. **Use in meetings**: Reference during feature discussions

## Integration with Other Skills

- **persona-definition**: Use for research-backed, official personas
- **improvement-proposals**: Use personas to inform feature specs
- **competitive-intelligence**: Understand what personas expect from market
- **product-evolution-analysis**: See how personas influenced past decisions

## Related Commands

- `/persona-definition` - Full persona research and documentation
- `/quick-competitive-scan` - See what features personas expect
- `/feature-impact-estimate` - Estimate feature value for persona

---

**Remember**: Quick personas are conversation starters, not research documents. Validate assumptions with real user research before major product bets.
