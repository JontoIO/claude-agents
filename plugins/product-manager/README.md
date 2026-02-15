# Product Manager Agent Plugin

A comprehensive product management agent that provides product strategy, competitive analysis, persona definition, improvement proposals, and changelog creation capabilities for any software product.

## Overview

The Product Manager agent helps you make informed product decisions by providing:
- **Strategic product evolution planning** with prioritized roadmaps
- **Competitive intelligence** with feature matrices and positioning analysis
- **Evidence-based user personas** using jobs-to-be-done framework
- **Prioritized improvement proposals** with RICE scoring and business cases
- **Compelling changelogs** optimized for different audiences

This agent is **product-type agnostic** and works with any repository: SaaS applications, open source projects, APIs, developer tools, mobile apps, enterprise software, and AI/ML products.

## When to Use This Agent

Use the Product Manager agent when you need to:
- Understand where your product is and where it should go next
- Research competitors and identify feature gaps or positioning opportunities
- Create user personas to guide product decisions
- Prioritize features and improvements with data-driven frameworks
- Communicate product changes effectively to users
- Make strategic product decisions with evidence and frameworks

## Capabilities

### 1. Product Evolution Analysis
Assess your product's current state, identify market opportunities, and create a strategic 3-12 month roadmap.

**What you get**:
- Current state assessment (features, maturity, activity)
- Market context and competitive landscape
- User journey mapping with pain points
- Gap analysis (capabilities vs needs)
- RICE-prioritized opportunities
- Quarterly roadmap with themes and milestones

**When to use**: Planning product direction, quarterly/annual roadmapping, identifying growth opportunities

### 2. Competitive Intelligence
Research competitors, build feature comparison matrices, and identify strategic positioning opportunities.

**What you get**:
- Competitor identification (direct, indirect, emerging)
- Feature comparison matrix across 5+ competitors
- Value proposition and pricing analysis
- SWOT analysis for top competitors
- Positioning map with white space opportunities
- Strategic recommendations with priorities

**When to use**: Understanding competitive landscape, planning feature parity, positioning decisions, market research

### 3. User Persona Definition
Create evidence-based personas with jobs-to-be-done mapping to guide product prioritization.

**What you get**:
- 3-5 detailed persona profiles
- Jobs-to-be-done analysis (functional, emotional, social)
- Persona validation against competitive users
- Feature-to-persona mapping
- Persona-specific priorities and messaging

**When to use**: Understanding target users, prioritizing features by audience, aligning team on who you're building for

### 4. Improvement Proposal Generation
Generate prioritized improvement ideas with business cases and implementation guidance.

**What you get**:
- 10-15 improvement proposals across categories
- RICE scoring and value-complexity matrix
- Top 5-10 detailed proposals with business cases
- Impact estimates (user, business, strategic)
- Effort estimates with dependencies and risks
- Go/no-go recommendations

**When to use**: Building product backlog, prioritizing features, creating PRDs, quarterly planning

### 5. Changelog Creation
Transform technical commits into compelling user-facing changelogs for multiple channels.

**What you get**:
- User-focused changelog (benefits over technical details)
- Multiple formats: GitHub release, in-app, newsletter, social media, blog post
- Storytelling that explains why changes matter
- Before/after framing
- Multi-audience optimization

**When to use**: Announcing releases, communicating updates, engaging users, building excitement

## Product Types Supported

The Product Manager agent adapts to any product type:

- **SaaS Applications**: B2B, B2C, PLG, enterprise sales models
- **Open Source Projects**: Libraries, frameworks, community-driven tools
- **APIs & Platforms**: REST, GraphQL, SDKs, integration platforms
- **Developer Tools**: CLI tools, IDEs, build systems, debugging tools
- **Mobile Applications**: iOS, Android, cross-platform apps
- **Enterprise Software**: On-premise, hybrid, compliance-heavy products
- **AI/ML Products**: Model APIs, training platforms, AI-powered features

## Available Skills

Skills are comprehensive, structured analyses that take 30-90 minutes to complete.

### `/product-manager:product-evolution-analysis`

**7-step framework** for comprehensive product evolution planning.

**Usage**:
```
Use the product-evolution-analysis skill to create a 12-month roadmap
```

**Steps**:
1. Current State Assessment
2. Market Context Discovery
3. User Journey Mapping
4. Gap Analysis
5. Opportunity Prioritization (RICE)
6. Evolution Roadmap (quarterly themes)
7. Recommendation Report

**Output**: Product evolution report with prioritized roadmap and top 5 opportunities

**Example**: See `examples/saas-project-management.md` for complete scenario

---

### `/product-manager:competitive-intelligence`

**7-step framework** for competitive research and positioning analysis.

**Usage**:
```
Run competitive-intelligence skill to research our top 5 competitors
```

**Steps**:
1. Competitor Identification
2. Feature Matrix Construction
3. Value Proposition Analysis
4. Pricing Intelligence
5. Strengths & Weaknesses Assessment (SWOT)
6. Strategic Positioning
7. Competitive Strategy Report

**Output**: Competitive intelligence report with feature matrix and strategic recommendations

**Example**: See all examples for competitive analysis sections

---

### `/product-manager:persona-definition`

**6-step framework** for evidence-based persona creation.

**Usage**:
```
Use persona-definition skill to create user personas for this product
```

**Steps**:
1. User Segmentation Discovery
2. Persona Research
3. Jobs-to-be-Done Framework
4. Persona Construction (3-5 personas)
5. Persona Validation
6. Application Framework (feature mapping)

**Output**: Detailed persona profiles with JTBD and feature prioritization

**Example**: See `examples/developer-tool-cli.md` for developer personas

---

### `/product-manager:improvement-proposals`

**6-step framework** for generating prioritized improvement proposals.

**Usage**:
```
Run improvement-proposals skill to generate feature ideas with RICE scores
```

**Steps**:
1. Opportunity Mining
2. Proposal Ideation (10-15 proposals)
3. Impact Assessment
4. Effort Estimation
5. Prioritization Framework (RICE, value-complexity)
6. Proposal Documentation (top 5-10 with business cases)

**Output**: Prioritized proposals with detailed business cases and go/no-go recommendations

**Example**: See `examples/open-source-library.md` for OSS sustainability proposals

---

### `/product-manager:changelog-creation`

**5-step framework** for creating multi-format changelogs.

**Usage**:
```
Use changelog-creation skill to create changelog for last month
```

**Steps**:
1. Change Discovery (git commits, PRs, issues)
2. User Impact Translation
3. Content Structuring
4. Storytelling Enhancement
5. Multi-Format Output (technical, user, newsletter, social, blog)

**Output**: User-facing changelogs optimized for different channels

**Example**: See `examples/saas-project-management.md` for 6 months of changelogs

## Available Commands

Commands are quick actions (3-10 minutes) for common PM tasks where speed matters more than depth.

### `quick-competitive-scan`

**5-10 minute** rapid competitor overview with feature parity check.

**Usage**:
```
/product-manager:quick-competitive-scan --competitors "Competitor1, Competitor2, Competitor3" --focus features
```

**Options**:
- `--competitors`: Comma-separated list (default: auto-detect)
- `--focus`: features, pricing, UX, performance

**Output**: Feature parity matrix, gap analysis, table stakes identification

**When to use**: Quick competitive check, sprint planning, stakeholder updates

---

### `quick-changelog`

**3-5 minute** user-facing changelog from recent commits.

**Usage**:
```
/product-manager:quick-changelog --since "1 week ago" --format markdown --audience users
```

**Options**:
- `--since`: Time period (default: "1 week ago")
- `--format`: markdown, slack, email, tweet
- `--audience`: users, developers, internal

**Output**: User-focused changelog in requested format

**When to use**: Weekly updates, sprint demos, quick announcements

---

### `persona-quick-reference`

**5 minute** basic persona profile generation.

**Usage**:
```
/product-manager:persona-quick-reference --persona-name "Developer Dan" --focus goals
```

**Options**:
- `--persona-name`: Name to use (default: infer from repo)
- `--focus`: goals, pain-points, tech-savvy, budget

**Output**: Basic persona profile with key characteristics

**When to use**: Quick team alignment, feature discussions, prioritization debates

---

### `feature-impact-estimate`

**3-5 minute** RICE score and go/no-go recommendation.

**Usage**:
```
/product-manager:feature-impact-estimate --feature "Bulk operations" --compare "Real-time sync, Dark mode"
```

**Options**:
- `--feature`: Feature to evaluate (required)
- `--compare`: Other features to compare against

**Output**: RICE score, go/no-go recommendation, comparison table

**When to use**: Sprint planning, prioritization decisions, quick estimates

## Complete Usage Walkthrough

Here's how to use the Product Manager agent for a typical product planning cycle:

### Step 1: Understand Current State

```
Load the product-manager agent and run product-evolution-analysis skill to assess our current state and create a roadmap
```

This gives you:
- Current product maturity and features
- Market opportunities
- Prioritized opportunities with RICE scores
- 12-month roadmap with quarterly themes

### Step 2: Research Competition

```
Use competitive-intelligence skill to research our top 3 competitors and identify feature gaps
```

This gives you:
- Feature comparison matrix
- Pricing analysis
- Strategic positioning recommendations
- White space opportunities

### Step 3: Define Your Users

```
Run persona-definition skill to create evidence-based user personas
```

This gives you:
- 3-5 detailed personas
- Jobs-to-be-done mapping
- Feature prioritization by persona value

### Step 4: Generate Improvement Ideas

```
Use improvement-proposals skill to generate prioritized feature proposals with business cases
```

This gives you:
- 10-15 proposals across categories
- RICE scores and prioritization tiers
- Top 5 proposals with detailed business cases

### Step 5: Execute and Communicate

```
As you ship features, use changelog-creation skill to announce updates to users
```

This gives you:
- User-facing changelogs
- Multiple formats (email, social, blog)
- Storytelling that builds excitement

### Step 6: Quick Actions Throughout

```
/product-manager:quick-competitive-scan --competitors "CompetitorX" --focus pricing
/product-manager:feature-impact-estimate --feature "New feature X"
/product-manager:quick-changelog --since "1 week ago" --format slack
```

Use commands for quick checks and updates between deeper analyses.

## Integration with Other Agents

The Product Manager agent works well alongside other specialized agents:

### Product Manager + Financial Advisor
**Scenario**: You identify opportunities → Financial estimates ROI and costs

**Workflow**:
1. PM: Run improvement-proposals to identify opportunities
2. Financial: Estimate development costs and revenue impact
3. PM: Refine priorities based on financial analysis
4. Financial: Create budget and forecast for roadmap

**Example**: "Use improvement-proposals to find opportunities, then have Financial Advisor estimate costs and ROI for top 3"

### Product Manager + Security Specialists
**Scenario**: Identify compliance requirements → Validate feasibility

**Workflow**:
1. PM: Competitive-intelligence reveals enterprise security needs
2. Security: Assess current security posture and gaps
3. PM: Prioritize security features based on feasibility
4. Security: Provide implementation guidance

### Product Manager + DevOps
**Scenario**: Plan infrastructure needs → Estimate operational costs

**Workflow**:
1. PM: Product-evolution-analysis identifies scaling needs
2. DevOps: Estimate infrastructure requirements and costs
3. PM: Factor infrastructure costs into roadmap prioritization

## Best Practices

### 1. Start with Context
Before diving into skills, help the agent understand your product:
- Share README, docs, or product overview
- Mention your product stage (MVP, growth, mature)
- Clarify your goals (growth, retention, enterprise, etc.)

### 2. Use Skills for Depth, Commands for Speed
- **Skills** (30-90 min): Comprehensive analysis, strategic decisions, quarterly planning
- **Commands** (3-10 min): Quick checks, sprint planning, stakeholder updates

### 3. Evidence Over Opinions
The agent grounds recommendations in:
- User feedback (issues, discussions)
- Competitive research (web search)
- Market data (industry trends)
- Repository analysis (commits, code)

**Ask for sources**: "Show me evidence for this recommendation"

### 4. Prioritize Ruthlessly
Not everything can be P0. Use frameworks:
- **RICE**: Quantitative prioritization
- **Value vs Complexity**: Visual prioritization
- **Kano Model**: Must-have vs delight features

**Focus on top 3-5**: Most teams can only execute 3-5 major initiatives per quarter.

### 5. Adapt to Your Product Type
The agent adapts methodology to your context:
- **SaaS**: Focus on retention, expansion, enterprise sales
- **Open Source**: Focus on sustainability, community, contributors
- **Dev Tools**: Focus on activation, DX, bottom-up adoption

**Be explicit**: "This is an open-source library" or "We're a B2B SaaS in growth stage"

### 6. Iterate and Update
Product management is continuous:
- **Quarterly**: Refresh product-evolution-analysis and roadmap
- **Monthly**: Quick competitive scans to track changes
- **Weekly**: Changelogs for releases and updates
- **As needed**: Personas, proposals when planning new features

### 7. Validate Assumptions
The agent makes educated guesses when data is limited:
- Validate personas with real users
- Test proposals with user interviews
- A/B test features before full rollout
- Track metrics to verify impact estimates

### 8. Share Widely
Product management outputs are valuable across the team:
- **Engineering**: Personas, priorities, roadmap
- **Design**: User journeys, pain points, JTBD
- **Marketing**: Positioning, messaging, changelogs
- **Sales**: Competitive intel, feature comparisons, roadmap

## Limitations

### What the Agent Does Well
✅ Analyze repository and codebase structure
✅ Research competitors and market trends (via web search)
✅ Apply PM frameworks (RICE, JTBD, Kano, etc.)
✅ Create structured analyses and reports
✅ Provide prioritization recommendations
✅ Generate user-facing content (changelogs, messaging)

### What the Agent Cannot Do
❌ Access private user analytics or behavior data
❌ Conduct user interviews or surveys
❌ Validate market assumptions without research
❌ Make final decisions (you decide, agent recommends)
❌ Track implementation or measure actual impact
❌ Access competitor products directly (only public info)

### When to Request Additional Data
The agent will ask for:
- **Analytics access**: If making data-driven decisions about user behavior
- **Business goals**: If prioritizing features without clear objectives
- **Technical constraints**: If proposing features without understanding feasibility
- **Budget information**: If estimating costs or ROI

### Accuracy Factors

**High Confidence** (80-100%):
- Repository analysis (code, commits, issues)
- Public competitor information (websites, docs, pricing)
- Standard PM frameworks (RICE, JTBD, Kano)
- Technical assessments (performance, architecture)

**Medium Confidence** (50-80%):
- User persona assumptions (without interviews)
- Impact estimates (without historical data)
- Competitive features (if private or hidden)
- Market trends (if data is limited)

**Low Confidence** (<50%):
- Effort estimates (without team involvement)
- Revenue projections (without business data)
- User adoption predictions (without testing)

## Examples

See the `examples/` directory for three complete scenarios:

### 1. SaaS Project Management Tool
**Product**: TaskFlow, a B2B project management SaaS
**Stage**: Growth stage, $8.5M ARR
**Challenges**: Feature parity vs incumbents, multi-stakeholder personas, 12-month roadmap to $15M

**File**: `examples/saas-project-management.md`

**Demonstrates**:
- Competitive analysis vs Asana, Monday.com, Clickup, Linear, Jira
- 4 personas (Engineering Manager, Creative Director, Operations, PM)
- 2 detailed proposals (Git Integration Hub, Creative Collaboration)
- 12-month roadmap with quarterly themes
- 6 months of changelogs

### 2. Open Source React Component Library
**Product**: Zenith UI, a React component library
**Stage**: Mature OSS, 45K stars, sustainability challenges
**Challenges**: Monetization, contributor burnout, competition from well-funded libraries

**File**: `examples/open-source-library.md`

**Demonstrates**:
- OSS-specific personas (including maintainer persona)
- Sustainability and monetization strategies
- Competitive analysis vs MUI, Chakra UI, Mantine, Ant Design, Radix, shadcn/ui
- Enterprise support program proposal
- Community-driven roadmap

### 3. Developer Tool CLI
**Product**: DevFlow CLI, a developer workflow tool
**Stage**: Early growth, $2M seed funding, 40% activation problem
**Challenges**: Activation (40% never use after install), freemium to enterprise, developer experience

**File**: `examples/developer-tool-cli.md`

**Demonstrates**:
- Developer tool personas (Startup Dev, Engineering Manager, Enterprise DevOps, OSS Maintainer)
- Activation optimization strategies
- Freemium → Enterprise upsell model
- Competitive analysis vs Docker, Podman, Devbox, Tilt
- Bottom-up adoption strategies

## Installation

From the Claude Code marketplace:

```bash
# Add marketplace (if not already added)
/plugin marketplace add jontoIO/claude-agents

# Install plugin
/plugin install product-manager@jontoio-claude-agents

# Verify installation
/agents
```

## Support

**Questions or feedback?**
- GitHub: https://github.com/jontoIO/claude-agents
- Issues: https://github.com/jontoIO/claude-agents/issues
- Email: contact@jonto.io

## License

MIT License - see LICENSE file for details

## Version

v1.0.0 - Initial release (February 2025)

---

**Built for product managers, founders, and teams** who want to make informed product decisions with data, frameworks, and strategic thinking.
