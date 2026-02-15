---
name: persona-definition
description: Create evidence-based user personas using 6-step methodology including user segmentation, jobs-to-be-done framework, persona construction with demographics and psychographics, and feature-to-persona mapping
---

# Persona Definition Skill

Create detailed, evidence-based user personas that help teams understand who they're building for, what users need, and how to prioritize features.

## When to Use This Skill

Use this skill when you need to:
- Understand who your users are and what they care about
- Segment users into distinct groups with different needs
- Apply jobs-to-be-done framework to understand user motivations
- Create personas to guide product decisions and prioritization
- Align team on target audience and user needs
- Inform marketing messaging and positioning
- Prioritize features based on persona value

## 6-Step Persona Definition Framework

### Step 1: User Segmentation Discovery (15-20 min)

**Objective**: Analyze the product to infer user types and segments

**Actions**:
1. **Feature Analysis**: Review product features (from README, docs, code)
   - Identify feature complexity levels (basic, intermediate, advanced)
   - Note collaboration vs individual features
   - Look for role-specific features (admin, viewer, contributor)
2. **Documentation Analysis**: Review docs for signals about users
   - Tutorials and guides (what skill levels are addressed?)
   - Use cases and examples (what scenarios are shown?)
   - FAQs (what questions do users ask?)
3. **Issue & Discussion Analysis**: Read GitHub issues, discussions, support requests
   - What problems do users report?
   - What features do they request?
   - What language do they use? (technical jargon vs plain language)
   - What do they mention about their context? (company size, use case, team)
4. **Initial Segmentation Hypotheses**: Based on signals, hypothesize user segments
   - By role: Developer, Designer, PM, Manager, End-user
   - By skill: Beginner, Intermediate, Expert
   - By use case: Personal projects, Team collaboration, Enterprise deployment
   - By company size: Individual, Startup, SMB, Enterprise
   - By context: Open source contributor, Commercial user, Student

**Output Format**:
```markdown
## User Segmentation Discovery

### Signals from Product Analysis

**Feature Complexity Spectrum**:
- **Basic features**: [List features accessible to beginners]
- **Intermediate features**: [List features requiring some expertise]
- **Advanced features**: [List power-user features]

**Collaboration Indicators**:
- [E.g., "Team sharing, role-based permissions, commenting" → Multiple user types]
- [E.g., "Single-player tool, no sharing features" → Individual users primarily]

**Role-Specific Features**:
- **Admin/Owner**: [Features only admins use]
- **Contributor/Editor**: [Features for content creators]
- **Viewer/Consumer**: [Read-only features]

### Signals from Documentation

**Tutorials Target Audience**:
- [E.g., "Quickstart assumes command-line knowledge" → Developer audience]
- [E.g., "Step-by-step with screenshots" → Less technical audience]

**Use Cases Highlighted**:
- [E.g., "Personal blog hosting, portfolio sites" → Individual creators]
- [E.g., "Enterprise documentation, team wikis" → Business teams]

### Signals from User Feedback

**Common User Archetypes (from issues/discussions)**:
- [E.g., "Solo developer building side projects"]
- [E.g., "Design team at startup collaborating on prototypes"]
- [E.g., "Enterprise IT managing deployment for 1000+ users"]

**Language Used**:
- [E.g., "Lots of technical jargon, CLI commands" → Technical users]
- [E.g., "Questions about basics, troubleshooting" → Less experienced users]

### Initial Segment Hypotheses

Based on evidence, likely user segments:
1. **[Segment 1]**: [E.g., "Solo developers building open source projects"]
2. **[Segment 2]**: [E.g., "Small teams (2-10) at startups collaborating"]
3. **[Segment 3]**: [E.g., "Enterprise teams (50+) with compliance needs"]
4. **[Segment 4]**: [E.g., "Students and learners exploring the tool"]
```

---

### Step 2: Persona Research (15-20 min)

**Objective**: Validate and enrich segment hypotheses with market research

**Actions**:
1. **Competitor User Research**: Web search for how competitors describe their users
   - "[competitor name] target audience"
   - "[competitor name] customer stories" or "case studies"
   - "[competitor name] pricing" (tiers often reveal user segments)
2. **Industry User Characteristics**: Web search for industry research
   - "[product category] user demographics"
   - "[product category] buyer persona"
   - Reports from Gartner, Forrester, industry blogs
3. **Community Insights**: Search forums, Reddit, Twitter, LinkedIn
   - "[product category] Reddit" (discussions reveal user contexts)
   - "[product type] for [use case]" (see who's asking and why)
   - Social profiles of users who mention the product
4. **Persona Patterns**: Identify common patterns across similar products
   - Demographics (age, role, industry, company size)
   - Goals and motivations
   - Pain points and frustrations
   - Preferred tools and workflows

**Output Format**:
```markdown
## Persona Research Findings

### Competitor User Profiles

**[Competitor 1] Target Users**:
- Primary segment: [E.g., "Mid-market B2B companies (50-500 employees)"]
- Key personas: [E.g., "Marketing managers, content creators, agency owners"]
- Messaging: [E.g., "Emphasizes ease-of-use for non-technical users"]

**[Competitor 2] Target Users**:
- Primary segment: [E.g., "Developers at startups and scale-ups"]
- Key personas: [E.g., "Full-stack developers, DevOps engineers"]
- Messaging: [E.g., "Emphasizes speed, CLI workflow, integrations"]

### Industry Insights

**[Product Category] User Demographics** (from [source]):
- **Age**: [E.g., "25-45 years old, mostly millennials"]
- **Roles**: [E.g., "50% developers, 30% designers, 20% product/business"]
- **Company Size**: [E.g., "40% startups (<50), 35% SMB (50-500), 25% enterprise (500+)"]
- **Industries**: [E.g., "Tech, SaaS, agencies, e-commerce"]

**Common Goals**:
- [E.g., "Speed up development workflow"]
- [E.g., "Improve collaboration with non-technical stakeholders"]
- [E.g., "Reduce costs vs enterprise tools"]

**Common Pain Points**:
- [E.g., "Existing tools too complex or expensive"]
- [E.g., "Difficulty onboarding team members"]
- [E.g., "Lack of integrations with existing stack"]

### Community Insights

**User Contexts (from forums/social)**:
- [E.g., "Solo founders building MVPs quickly"]
- [E.g., "Remote teams needing async collaboration"]
- [E.g., "Agencies managing multiple client projects"]

**Direct Quotes** (capturing user voice):
- "[Quote showing user motivation or pain point]"
- "[Quote revealing user context or priorities]"
```

---

### Step 3: Jobs-to-be-Done Framework (15-20 min)

**Objective**: Define the jobs users are hiring the product to do

**Actions**:
1. **Functional Jobs**: What tasks do users need to complete?
   - Main job (the primary reason to use the product)
   - Related jobs (adjacent tasks users do)
   - Outcome expected (what does success look like?)
2. **Emotional Jobs**: How do users want to feel?
   - Confidence, control, creativity, recognition, belonging, etc.
   - Fears they want to avoid (anxiety, frustration, embarrassment)
3. **Social Jobs**: How do users want to be perceived?
   - By peers, by managers, by clients, by the industry
   - Identity they want to project (innovative, reliable, efficient, etc.)
4. **Situational Context**: When/where do these jobs arise?
   - Triggering events (what causes them to seek a solution?)
   - Constraints (time, budget, skills, team size)
   - Alternatives considered (what else could they use?)

**Output Format**:
```markdown
## Jobs-to-be-Done Analysis

### Functional Jobs

**Main Job**:
When [situation], I want to [motivation], so I can [outcome].
- Example: "When starting a new project, I want to set up infrastructure quickly, so I can focus on building features."

**Related Jobs**:
1. [E.g., "Collaborate with teammates on [task]"]
2. [E.g., "Track progress and monitor [metrics]"]
3. [E.g., "Integrate with [other tools] in my workflow"]

**Success Criteria** (how users measure if the job is done well):
- [E.g., "Project set up in <15 minutes"]
- [E.g., "Zero configuration required"]
- [E.g., "All teammates can contribute without setup friction"]

### Emotional Jobs

**Users want to feel**:
- [E.g., "**In control**: Confident they understand what's happening, no surprises"]
- [E.g., "**Productive**: Making progress, not stuck on setup or troubleshooting"]
- [E.g., "**Creative**: Able to experiment and iterate quickly without friction"]
- [E.g., "**Secure**: Trust that their work is safe, backed up, compliant"]

**Users want to avoid feeling**:
- [E.g., "**Overwhelmed**: Complexity, too many options, unclear docs"]
- [E.g., "**Frustrated**: Bugs, slow performance, poor UX"]
- [E.g., "**Embarrassed**: Breaking things, looking incompetent in front of team"]

### Social Jobs

**Users want to be seen as**:
- [E.g., "**Competent**: By managers and peers as someone who delivers"]
- [E.g., "**Modern**: Using cutting-edge tools and practices"]
- [E.g., "**Reliable**: Someone the team can depend on"]
- [E.g., "**Efficient**: Getting more done with less effort"]

### Situational Context

**Triggering Events** (what causes users to seek this solution):
- [E.g., "Starting a new project or company"]
- [E.g., "Current tool is too expensive as team grows"]
- [E.g., "Frustrated with slow, complex incumbent tool"]
- [E.g., "Team growing, need better collaboration features"]

**Constraints**:
- [E.g., "**Budget**: Limited funds, need affordable or free option"]
- [E.g., "**Time**: Need to launch quickly, can't spend weeks on setup"]
- [E.g., "**Skills**: Non-technical users on team, need simple UI"]
- [E.g., "**Compliance**: Industry regulations (HIPAA, SOC 2, GDPR)"]

**Alternatives Considered**:
- [E.g., "Build in-house (too slow, expensive)"]
- [E.g., "[Competitor 1] (too complex, steep learning curve)"]
- [E.g., "[Competitor 2] (too expensive for our stage)"]
- [E.g., "Stick with manual process (doesn't scale)"]
```

---

### Step 4: Persona Construction (20-25 min)

**Objective**: Create 3-5 detailed persona profiles

**Actions**:
1. **Select Primary Personas**: Choose 3-5 most important user segments
   - Focus on segments that represent 70-80% of users or revenue
   - Include at least one aspirational persona (future target user)
2. **Persona Template**: For each persona, document:
   - **Name & Photo**: Give them a memorable name (e.g., "Developer Dan", "Manager Maria")
   - **Role & Demographics**: Job title, age range, company size, industry
   - **Background & Context**: Experience level, team structure, daily workflow
   - **Goals & Motivations**: What they're trying to achieve (functional, emotional, social jobs)
   - **Pain Points & Frustrations**: Problems with current solutions
   - **Behaviors & Preferences**: How they work, tools they use, learning style
   - **Quotes**: 2-3 quotes capturing their voice and priorities
   - **Tech Savviness**: Skill level with tools like this product
3. **Persona Prioritization**: Rank personas by:
   - **Primary**: Core target audience, highest volume or strategic importance
   - **Secondary**: Important but smaller segment or lower priority
   - **Aspirational**: Future target as product matures or expands

**Output Format**:
```markdown
## User Personas

### Persona 1: [Name, e.g., "Developer Dan"] (Primary)

**Role & Demographics**:
- **Job Title**: [E.g., "Senior Full-Stack Developer"]
- **Age**: [E.g., "28-38"]
- **Company**: [E.g., "Startup or scale-up (10-100 employees)"]
- **Industry**: [E.g., "SaaS, fintech, e-commerce"]
- **Location**: [E.g., "Urban tech hubs, remote-friendly"]

**Background & Context**:
- 5-10 years of professional development experience
- Works on small, fast-moving team (3-8 engineers)
- Owns features end-to-end (frontend, backend, deployment)
- Juggles multiple projects and priorities simultaneously
- Values speed and autonomy over process and governance

**Goals & Motivations**:
- **Functional**: Ship features quickly, maintain high code quality, minimize operational overhead
- **Emotional**: Feel productive and in control, avoid getting blocked by tools or infrastructure
- **Social**: Be seen as a high-performing, modern engineer who uses best practices

**Pain Points & Frustrations**:
- "Existing tools are overkill for our needs - too complex, too many features we don't use"
- "Setup takes forever - I want to start coding, not spend days on configuration"
- "Documentation is either too basic or too technical, hard to find the info I need"
- "Poor developer experience - clunky CLI, slow builds, inconsistent behavior"

**Behaviors & Preferences**:
- Prefers CLI and keyboard shortcuts over GUI
- Learns by doing, prefers examples over long explanations
- Active in developer communities (GitHub, Stack Overflow, Discord)
- Willing to adopt new tools if they promise 10x improvement
- Skeptical of marketing hype, wants proof (benchmarks, demos, source code)

**Quotes**:
- "I just want it to work so I can focus on building features, not fighting tools."
- "If I can't get value in 15 minutes, I'm moving on to the next option."
- "Show me the code. I'll read the README and examples before docs."

**Tech Savviness**: ⚙️⚙️⚙️⚙️⚙️ (Expert - very comfortable with technical tools)

**Priority**: 🔴 Primary (represents 40% of users, core target audience)

---

### Persona 2: [Name, e.g., "Manager Maria"] (Secondary)

**Role & Demographics**:
- **Job Title**: [E.g., "Engineering Manager / Tech Lead"]
- **Age**: [E.g., "32-45"]
- **Company**: [E.g., "SMB to mid-market (50-500 employees)"]
- **Industry**: [E.g., "B2B SaaS, enterprise software"]
- **Location**: [E.g., "Mix of urban offices and remote"]

**Background & Context**:
- Manages team of 5-15 engineers
- Still codes occasionally but mostly reviews and manages
- Responsible for team velocity, quality, and morale
- Budget owner for team tools and infrastructure
- Balances technical decisions with business priorities

**Goals & Motivations**:
- **Functional**: Improve team productivity, reduce friction, enable self-service, ensure security and compliance
- **Emotional**: Feel confident in technical choices, reduce stress from firefighting, empower team
- **Social**: Be seen as an effective leader who enables their team, respected by both engineers and executives

**Pain Points & Frustrations**:
- "Need tools that scale as the team grows without breaking the bank"
- "Onboarding new engineers takes 2-3 days - too long"
- "Hard to get visibility into what the team is doing without micromanaging"
- "Security and compliance are becoming requirements, but most tools are expensive or complex"

**Behaviors & Preferences**:
- Evaluates tools for team fit (ease of adoption, cost, support)
- Values documentation, support, and community for helping the team
- Needs to justify costs to leadership with ROI
- Prefers tools that "just work" and require minimal maintenance
- Appreciates dashboards and reporting for team visibility

**Quotes**:
- "If my team loves it and it saves them time, I'll find the budget."
- "Onboarding should take 30 minutes, not 3 days. Time to productivity matters."
- "I need tools that scale from 5 to 50 engineers without replatforming."

**Tech Savviness**: ⚙️⚙️⚙️⚙️ (Advanced - comfortable but not coding daily)

**Priority**: 🟡 Secondary (represents 25% of users, influences purchasing decisions)

---

### Persona 3: [Name, e.g., "Startup Steve"] (Primary)

**Role & Demographics**:
- **Job Title**: [E.g., "Solo Founder / Indie Hacker"]
- **Age**: [E.g., "25-40"]
- **Company**: [E.g., "Solo or 2-3 person team, pre-seed"]
- **Industry**: [E.g., "Indie SaaS, side projects, bootstrapped startups"]
- **Location**: [E.g., "Anywhere, often remote/nomadic"]

**Background & Context**:
- Wearing multiple hats (developer, designer, marketer, support)
- Limited budget, often using free tiers or cheap alternatives
- Building MVP to validate idea quickly
- Works nights/weekends if side project, or full-time if funded
- Learning as they go, not an expert in everything

**Goals & Motivations**:
- **Functional**: Build and launch quickly, minimize costs, validate idea, iterate fast
- **Emotional**: Feel empowered to build without needing a team, avoid overwhelm from complexity
- **Social**: Be seen as resourceful and scrappy, part of the indie/startup community

**Pain Points & Frustrations**:
- "Enterprise tools price me out - I'm one person, not a 100-person company"
- "I'm not a DevOps expert, I just want to deploy my app and move on"
- "Too many tools require credit card upfront - I want to try before committing"
- "Documentation assumes I know everything - I need hand-holding for non-core skills"

**Behaviors & Preferences**:
- Highly price-sensitive, loves free tiers and open source
- DIY mentality, willing to learn but wants the fastest path
- Active in indie hacker / maker communities (Twitter, Indie Hackers, Reddit)
- Shares journey publicly, posts wins and struggles
- Loyal to products that help them succeed early on

**Quotes**:
- "I'll use anything that's free or cheap and gets me to launch faster."
- "I don't need all the enterprise features - just let me get started easily."
- "If it saves me even 2 hours, it's worth it at this stage."

**Tech Savviness**: ⚙️⚙️⚙️ (Intermediate - knows enough to be dangerous)

**Priority**: 🔴 Primary (represents 30% of users, evangelists and early adopters)

---

### Persona 4: [Name, e.g., "Enterprise Emma"] (Aspirational)

**Role & Demographics**:
- **Job Title**: [E.g., "Director of Engineering / Platform Lead"]
- **Age**: [E.g., "35-50"]
- **Company**: [E.g., "Enterprise (500+ employees)"]
- **Industry**: [E.g., "Finance, healthcare, large tech companies"]
- **Location**: [E.g., "Global, distributed teams"]

**Background & Context**:
- Oversees multiple teams (50-200+ engineers)
- Responsible for platform strategy, architecture, and governance
- Long procurement cycles, multiple stakeholders (security, legal, finance)
- Must ensure compliance, security, and reliability at scale
- Risk-averse, needs proven solutions with strong support

**Goals & Motivations**:
- **Functional**: Standardize tooling across org, ensure security and compliance, minimize operational risk
- **Emotional**: Feel confident in choices, avoid career risk from bad decisions, reduce stress from outages
- **Social**: Be seen as strategic leader, trusted by C-suite, respected by engineering org

**Pain Points & Frustrations**:
- "We need enterprise features: SSO, RBAC, audit logs, SLAs, dedicated support"
- "Procurement takes 6-12 months - need vendor to be patient and professional"
- "Can't use tools that don't meet compliance standards (SOC 2, HIPAA, GDPR)"
- "If it goes down, I get the call at 2am - reliability is non-negotiable"

**Behaviors & Preferences**:
- Requires vendor vetting (security questionnaires, legal review, reference calls)
- Values white-glove support and dedicated account manager
- Willing to pay premium for reliability, security, and support
- Influenced by industry analysts (Gartner, Forrester), peer recommendations
- Prefers gradual rollout with training and change management support

**Quotes**:
- "We're not buying software, we're buying a relationship. Support and reliability matter more than features."
- "I need to see SOC 2 certification and pass a security review before we can even pilot."
- "Show me how this scales to 10,000 users across 20 teams in 5 countries."

**Tech Savviness**: ⚙️⚙️⚙️ (Intermediate to advanced - strategic, not hands-on)

**Priority**: 🔵 Aspirational (target for future growth, 5% of users today but high LTV)

---

### Persona Priority Summary

| Persona | Priority | % of Users | Revenue Impact | Why This Matters |
|---------|----------|------------|----------------|------------------|
| Developer Dan | 🔴 Primary | 40% | Medium | Core audience, high volume, evangelists |
| Startup Steve | 🔴 Primary | 30% | Low-Medium | Early adopters, community builders, word-of-mouth |
| Manager Maria | 🟡 Secondary | 25% | High | Purchasing decision-maker, scales with team growth |
| Enterprise Emma | 🔵 Aspirational | 5% | Very High | Future growth, high LTV, but requires enterprise features |

**Primary Focus**: Build for Developer Dan and Startup Steve - they are the majority of users today, provide feedback quickly, and spread word-of-mouth.

**Secondary Consideration**: Keep Manager Maria happy - she makes purchasing decisions and can bring the entire team or block adoption.

**Long-term Investment**: Prepare for Enterprise Emma - she represents highest revenue potential, but requires significant product maturity (security, compliance, scalability, support).
```

---

### Step 5: Persona Validation (10-15 min)

**Objective**: Cross-reference personas with competitive users and market data

**Actions**:
1. **Competitor Persona Check**: Do competitors target similar personas?
   - Review competitor customer stories, case studies, testimonials
   - Check competitor pricing tiers (who they're targeting by price)
   - Note any personas competitors target that you haven't considered
2. **Market Data Validation**: Search for industry reports or surveys
   - "[product category] user survey"
   - "[product category] buyer persona research"
   - Analyst reports (Gartner, Forrester) if available
3. **Persona Completeness**: Ensure each persona has:
   - Clear job-to-be-done mapped to them
   - Distinct needs from other personas
   - Sufficient detail to guide product decisions
4. **Reality Check**: Ask yourself:
   - Do these personas represent 70%+ of current users?
   - Can we realistically serve all these personas with one product?
   - Are there conflicting needs between personas? (If yes, may need to narrow focus)

**Output Format**:
```markdown
## Persona Validation

### Cross-Check with Competitors

**[Competitor 1] Targets**:
- Matches our "Developer Dan" persona closely
- Also targets "Manager Maria" with team features and pricing
- Does NOT seem to target "Startup Steve" (no free tier, expensive entry)

**[Competitor 2] Targets**:
- Focuses heavily on "Enterprise Emma" (enterprise features, high prices)
- Less emphasis on "Developer Dan" (complex UI, less dev-friendly)

**[Competitor 3] Targets**:
- Similar to our "Startup Steve" persona (free tier, indie-friendly)
- Growing into "Developer Dan" with more advanced features

**Competitive Gaps**:
- Our focus on both "Developer Dan" AND "Startup Steve" is relatively unique
- "Manager Maria" is common target - table stakes features needed
- "Enterprise Emma" is long-term play, not immediate competitive threat

### Market Data Validation

**[Industry Report/Survey] Findings**:
- [E.g., "60% of [category] users are developers at companies <500 employees"] → Validates "Developer Dan" and "Startup Steve" focus
- [E.g., "Ease of use is #1 buying criteria for 70% of users"] → Validates persona pain points about complexity
- [E.g., "Enterprise adoption growing 30% YoY"] → Validates "Enterprise Emma" as aspirational

### Persona Completeness Check

| Persona | Clear JTBD? | Distinct Needs? | Sufficient Detail? | Reality Check |
|---------|-------------|-----------------|-------------------|---------------|
| Developer Dan | ✅ Yes | ✅ Unique | ✅ Detailed | ✅ Represents 40% |
| Manager Maria | ✅ Yes | ✅ Unique | ✅ Detailed | ✅ Purchasing influence |
| Startup Steve | ✅ Yes | ✅ Unique | ✅ Detailed | ✅ Represents 30% |
| Enterprise Emma | ✅ Yes | ✅ Unique | ✅ Detailed | ⚠️ Only 5% today |

### Potential Conflicts & Trade-offs

**Conflict 1: Simplicity vs Power**
- "Startup Steve" wants simplicity, "Developer Dan" wants power and flexibility
- **Resolution**: Layer features - simple by default, advanced options available
- **Example**: Sensible defaults, but allow configuration for power users

**Conflict 2: Free vs Enterprise**
- "Startup Steve" needs generous free tier, "Enterprise Emma" expects premium pricing
- **Resolution**: Freemium model - free for individuals, paid for teams/enterprises
- **Example**: Free up to 5 users, pricing kicks in for collaboration features

**Conflict 3: Self-Serve vs White-Glove**
- "Developer Dan" wants self-serve, "Enterprise Emma" expects account managers
- **Resolution**: Tiered support - community support for free/low tiers, dedicated for enterprise
- **Example**: Docs + community for open source, SLA + AM for enterprise contracts

**Strategic Choice**:
Focus product on "Developer Dan" and "Startup Steve" (70% of users) first. Build core that serves them exceptionally well. Add "Manager Maria" features (team collaboration, admin) in 6-12 months. Pursue "Enterprise Emma" (SSO, compliance, support) in 12-24 months once product-market fit is proven.
```

---

### Step 6: Application Framework (15-20 min)

**Objective**: Map features to persona needs and prioritize by persona value

**Actions**:
1. **Feature-to-Persona Mapping**: For each major feature, identify:
   - Which personas care about it (Primary, Secondary, Not relevant)
   - Why they care (what job does it help with?)
   - Impact (High, Medium, Low)
2. **Persona-Driven Prioritization**: Rank features by:
   - Number of personas who value it
   - Importance to primary personas
   - Strategic fit (does it differentiate or just achieve parity?)
3. **Persona-Specific Roadmap**: For each persona, list:
   - Current strengths (features that delight them)
   - Current gaps (missing features that frustrate them)
   - Top 3 priorities to better serve this persona
4. **Messaging Framework**: For each persona, define:
   - Primary message (headline value prop)
   - Key benefits (what they care about most)
   - Proof points (how you demonstrate value)

**Output Format**:
```markdown
## Feature-to-Persona Mapping

| Feature | Developer Dan | Manager Maria | Startup Steve | Enterprise Emma | Strategic Value |
|---------|---------------|---------------|---------------|-----------------|-----------------|
| Quick setup (<15min) | 🔴 Critical | 🟡 Important | 🔴 Critical | 🟢 Nice | Differentiator (vs complex competitors) |
| CLI workflow | 🔴 Critical | 🟢 Nice | 🟡 Important | ⚫ Not relevant | Differentiator (dev experience) |
| Free tier (generous) | 🟡 Important | 🟢 Nice | 🔴 Critical | ⚫ Not relevant | Differentiator (vs expensive competitors) |
| Team collaboration | 🟡 Important | 🔴 Critical | 🟢 Nice | 🟡 Important | Parity (table stakes) |
| SSO / SAML | ⚫ Not relevant | 🟢 Nice | ⚫ Not relevant | 🔴 Critical | Aspirational (enterprise play) |
| Real-time sync | 🟡 Important | 🟡 Important | 🟡 Important | 🟡 Important | Differentiator (modern expectation) |
| Integrations (API) | 🔴 Critical | 🟡 Important | 🟡 Important | 🟡 Important | Parity (ecosystem moat) |

**Legend**:
- 🔴 Critical: Must-have, deal-breaker if missing
- 🟡 Important: Strong preference, impacts decision
- 🟢 Nice: Appreciated but not deciding factor
- ⚫ Not relevant: Doesn't care or doesn't apply

---

## Persona-Driven Feature Prioritization

### High Priority (Serves multiple primary personas)
1. **Quick setup (<15 min)**: Critical for Developer Dan (40%) and Startup Steve (30%) = 70% of users
2. **CLI workflow**: Critical for Developer Dan (40%) + Important for Startup Steve (30%) = delight 70%
3. **Integrations/API**: Critical for Developer Dan (40%) + Important for all others = ecosystem moat

### Medium Priority (Serves secondary personas or nice-to-have for primary)
4. **Team collaboration**: Critical for Manager Maria (25%), Important for Developer Dan (40%) = purchasing unlock
5. **Real-time sync**: Important for all personas, modern expectation, competitive parity
6. **Free tier (generous)**: Critical for Startup Steve (30%), differentiator vs expensive competitors

### Low Priority (Aspirational personas or niche needs)
7. **SSO/SAML**: Critical for Enterprise Emma (5% today), but required for long-term growth
8. **Advanced reporting**: Important for Manager Maria and Enterprise Emma, not urgent for primary personas

---

## Persona-Specific Roadmap

### Developer Dan (Primary, 40% of users)

**Current Strengths** (features that already delight):
- ✅ Fast CLI workflow
- ✅ Good documentation with code examples
- ✅ Integrations with dev tools (GitHub, VS Code, etc.)

**Current Gaps** (missing features causing frustration):
- ❌ No bulk operations (must repeat commands)
- ❌ Performance degrades with large datasets
- ❌ Limited customization options

**Top 3 Priorities**:
1. **Performance optimization for large datasets**: (Effort: 4 weeks) → Retain power users
2. **Bulk operations and automation**: (Effort: 3 weeks) → Improve productivity for daily workflows
3. **Advanced configuration options**: (Effort: 2 weeks) → Enable customization without complexity

---

### Manager Maria (Secondary, 25% of users)

**Current Strengths**:
- ✅ Team can self-serve and onboard quickly
- ✅ Affordable pricing for small teams

**Current Gaps**:
- ❌ No visibility into team usage or activity
- ❌ Lack of role-based access control
- ❌ No audit logs or compliance features

**Top 3 Priorities**:
1. **Team dashboard and analytics**: (Effort: 5 weeks) → Provide visibility without micromanagement
2. **Role-based permissions (admin/member/viewer)**: (Effort: 4 weeks) → Required for larger teams
3. **Activity logs and audit trail**: (Effort: 3 weeks) → Trust and compliance for managers

---

### Startup Steve (Primary, 30% of users)

**Current Strengths**:
- ✅ Generous free tier
- ✅ Quick to get started
- ✅ Good community and documentation

**Current Gaps**:
- ❌ Requires credit card for any advanced features (friction)
- ❌ No templates or starter kits for common use cases
- ❌ Limited tutorials for non-expert users

**Top 3 Priorities**:
1. **No credit card required for trial**: (Effort: 1 week) → Reduce signup friction
2. **Templates and starter kits**: (Effort: 3 weeks) → Speed up time-to-value
3. **Beginner-friendly tutorials**: (Effort: 2 weeks) → Lower learning curve

---

### Enterprise Emma (Aspirational, 5% of users)

**Current Strengths**:
- ✅ Product is stable and reliable
- ✅ API allows custom integrations

**Current Gaps**:
- ❌ No SSO (SAML, OAuth)
- ❌ No compliance certifications (SOC 2, HIPAA)
- ❌ No dedicated support or SLA
- ❌ No enterprise admin features (user provisioning, etc.)

**Top 3 Priorities** (12-24 month roadmap):
1. **SSO and enterprise authentication**: (Effort: 8 weeks) → Requirement for enterprise sales
2. **SOC 2 Type II certification**: (Effort: 6 months) → Trust and compliance
3. **Enterprise support tier with SLA**: (Effort: ongoing) → Required for mission-critical usage

---

## Persona-Based Messaging Framework

### Developer Dan
**Primary Message**: "The fastest way to [core value] without the complexity."

**Key Benefits**:
- ⚡ Quick setup (15 minutes, not 2 days)
- 🛠️ CLI-first, integrates with your existing workflow
- 📚 Docs with code examples, not marketing fluff

**Proof Points**:
- "From zero to deployed in 15 minutes"
- "4.8/5 developer experience rating"
- "Used by 10,000+ developers at fast-moving startups"

---

### Manager Maria
**Primary Message**: "Empower your team to ship faster, without breaking the bank."

**Key Benefits**:
- 👥 Self-serve onboarding, no IT involvement needed
- 💰 Affordable pricing that scales with your team
- 📊 Visibility into team activity without micromanagement

**Proof Points**:
- "Teams onboard in 30 minutes, not 3 days"
- "$15/user/month vs $50+ industry average"
- "4.7/5 ease-of-use rating from managers"

---

### Startup Steve
**Primary Message**: "Build and launch your MVP faster, for free."

**Key Benefits**:
- 🆓 Generous free tier (no credit card required)
- 🚀 Launch in hours, not weeks
- 🤝 Join 5,000+ indie hackers and founders

**Proof Points**:
- "Free forever for solo projects"
- "From idea to live app in one weekend"
- "Featured on Indie Hackers, Product Hunt, HN"

---

### Enterprise Emma
**Primary Message**: "Enterprise-grade reliability and security, without enterprise complexity."

**Key Benefits**:
- 🔒 SOC 2 Type II, HIPAA, GDPR compliant
- 🛡️ SSO, RBAC, audit logs, 99.9% SLA
- 👔 Dedicated account manager and support

**Proof Points**:
- "Trusted by Fortune 500 companies"
- "99.95% uptime over last 12 months"
- "24/7 support with <1hr response time"
```

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **Segmentation**: Identified 4-6 distinct user segments based on evidence
- [ ] **Research**: Validated segments with competitor research and market data
- [ ] **Jobs-to-be-Done**: Defined functional, emotional, and social jobs for each segment
- [ ] **Personas**: Created 3-5 detailed personas with demographics, goals, pain points, behaviors, quotes
- [ ] **Prioritization**: Ranked personas (primary, secondary, aspirational) with rationale
- [ ] **Validation**: Cross-checked personas against competitive users and market data
- [ ] **Feature mapping**: Mapped major features to persona needs with impact levels
- [ ] **Roadmap**: Identified top 3 priorities for each primary persona
- [ ] **Messaging**: Defined persona-specific value propositions and proof points
- [ ] **Evidence-based**: All persona characteristics grounded in repository analysis, user feedback, or market research

---

## Tips for Effective Persona Definition

1. **Avoid stereotypes**: Base personas on real signals from users, not assumptions
2. **Use quotes**: Direct quotes from users (issues, forums, reviews) bring personas to life
3. **Focus on jobs-to-be-done**: Goals and motivations matter more than demographics
4. **Limit to 3-5 personas**: Too many personas = decision paralysis
5. **Distinguish clearly**: Each persona should have distinct needs; if they're too similar, merge them
6. **Prioritize ruthlessly**: Not all personas are equal; focus on primary personas (70%+ of impact)
7. **Make them actionable**: Teams should be able to answer "What would Developer Dan want?" when making decisions
8. **Update regularly**: Personas evolve as product and market mature; refresh quarterly
9. **Socialize widely**: Share personas with entire team (eng, design, marketing, sales) for alignment
10. **Test with real users**: Validate personas by showing them to actual users - do they recognize themselves?

---

## Integration with Other Skills

This skill works well with:

- **product-evolution-analysis**: Use personas to prioritize roadmap opportunities
- **competitive-intelligence**: Understand who competitors are targeting and why
- **improvement-proposals**: Generate feature ideas tailored to persona needs
- **changelog-creation**: Write user-facing announcements that speak to persona language and priorities

---

*Use this skill whenever you need to deeply understand your users, make persona-driven product decisions, or align your team on who you're building for.*
