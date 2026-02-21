# CEO Agent

The CEO orchestrator agent that coordinates all JontoIO marketplace agents to answer complex, multi-dimensional business questions with executive-level strategic guidance.

## Overview

The CEO agent is the command center of the JontoIO plugin ecosystem. Rather than answering questions from a single domain, it:

1. **Detects** which companion agents are installed
2. **Decomposes** complex questions into domain sub-tasks
3. **Delegates** to financial-advisor, product-manager, tax-advisor, and ai-specialist in parallel
4. **Synthesizes** all outputs into a single CEO-level recommendation
5. **Surfaces** cross-domain conflicts, dependencies, and gaps

The CEO agent also works standalone with graceful degradation — alerting when no marketplace agents are found, and flagging which agents would improve any given analysis.

## Works Best With

| Agent | Contribution |
|-------|-------------|
| `financial-advisor` | Costs, runway, revenue modeling, break-even |
| `product-manager` | Market fit, roadmap, competitive landscape, personas |
| `tax-advisor` | Compliance, VAT/IVA, jurisdiction setup, filing deadlines |
| `ai-specialist` | Technical health, test coverage, prompt optimization, tech debt |

**Install all four for full orchestration**:

```bash
/plugin install financial-advisor@jontoio-claude-agents
/plugin install product-manager@jontoio-claude-agents
/plugin install tax-advisor@jontoio-claude-agents
/plugin install ai-specialist@jontoio-claude-agents
/plugin install ceo@jontoio-claude-agents
```

## Key Features

### Multi-Agent Orchestration
Asks the right question to the right agent. A question like *"Should we launch next week?"* triggers:
- product-manager for feature completeness and UX readiness
- financial-advisor for pricing, runway, and launch costs
- tax-advisor for legal entity, privacy policy, and VAT setup
- ai-specialist for critical bugs, test coverage, and monitoring

### Graceful Degradation
Works with 0-4 companion agents. When agents are missing, the CEO:
- Proceeds with available agents
- Flags which domains were not formally assessed
- Recommends which agents to install and what analysis they would add

### Cross-Domain Conflict Resolution
When agents disagree, the CEO surfaces the conflict explicitly and resolves it — never leaves the user with "it depends" without a lean.

### Executive Communication Style
- Leads with the decision, not the analysis
- Uses traffic-light dashboards (🟢/🟡/🔴) for status
- Tables for multi-domain comparisons
- Quantifies everything; states confidence level when data is limited

## Available Skills

### [`strategic-assessment`](./skills/strategic-assessment/SKILL.md)
Full company or project situational analysis with SWOT, cross-domain synthesis, and prioritized actions.

**Trigger**: "Assess our company", "Where do we stand?", "Run a SWOT", "Situational analysis"

---

### [`production-readiness-analysis`](./skills/production-readiness-analysis/SKILL.md)
Launch readiness decision with traffic-light dashboard, weighted scorecard, and 30-day checklist.

**Trigger**: "Are we ready to launch?", "Production go/no-go", "Is [product] production-ready?"

---

### [`opportunity-analysis`](./skills/opportunity-analysis/SKILL.md)
Business opportunity evaluation with market sizing, financial modeling, and Pursue/Pass verdict.

**Trigger**: "Should we build X?", "Is market Y worth entering?", "Should we pivot?"

---

### [`executive-briefing`](./skills/executive-briefing/SKILL.md)
Multi-agent executive summary for board meetings, investor calls, and quarterly reviews.

**Trigger**: "Brief me on...", "Prepare me for a board meeting", "Quarterly review"

---

### [`company-roadmap-planning`](./skills/company-roadmap-planning/SKILL.md)
Cross-functional strategic roadmap integrating product, financial, compliance, and technical milestones.

**Trigger**: "Create a roadmap", "Plan the next 6/12 months", "What should we focus on?"

---

## Available Commands

### `/ceo:quick-health-check [focus-area]`
2-3 minute company health snapshot with traffic-light status per domain, top 3 risks, and one immediate action.

```bash
/ceo:quick-health-check
/ceo:quick-health-check financial
/ceo:quick-health-check "launch readiness"
```

---

### `/ceo:production-go-nogo [product-name]`
Quick launch readiness verdict with up to 5 critical blockers and estimated time to production-ready.

```bash
/ceo:production-go-nogo
/ceo:production-go-nogo "TaskFlow v1.0"
/ceo:production-go-nogo "payment module"
```

---

### `/ceo:opportunity-scan "[opportunity description]"`
Rapid opportunity evaluation with a 1-10 score and Explore / Pilot / Pass recommendation.

```bash
/ceo:opportunity-scan "Launch mobile app for field service workers"
/ceo:opportunity-scan "Pivot from B2B SaaS to developer API"
/ceo:opportunity-scan "Build HR module to compete with BambooHR"
```

---

### `/ceo:weekly-ceo-briefing [week-ending-date]`
Weekly executive summary with metrics, decisions made, decisions pending, next week priorities, and risks to watch.

```bash
/ceo:weekly-ceo-briefing
/ceo:weekly-ceo-briefing 2026-02-21
/ceo:weekly-ceo-briefing "last week"
```

---

## Example Scenarios

### Scenario 1: "Should we launch?"

```bash
# User: "We've had 40 beta users for 6 weeks. Can we launch publicly?"
# CEO agent: runs production-readiness-analysis skill
# Output: NO-GO verdict with 5 critical blockers and 30-day launch plan
```

See the full example: [Production Launch Decision](./examples/production-launch-decision.md)

---

### Scenario 2: "What's our strategic position?"

```bash
# User: "Give me a full assessment of where we stand"
# CEO agent: runs strategic-assessment skill
# Output: SWOT, domain findings table, prioritized actions
```

---

### Scenario 3: "Should we build an API?"

```bash
# Via command (quick scan):
/ceo:opportunity-scan "Expose a developer API for our core SaaS functionality"

# Via skill (full analysis):
# User: "Evaluate whether to build a developer API"
# CEO agent: runs opportunity-analysis skill
```

---

### Scenario 4: Monday Morning Briefing

```bash
/ceo:weekly-ceo-briefing
# Output: Week summary, metrics, pending decisions, this week's priorities, risks
```

---

## Usage Examples

### Basic Invocation

```bash
# Open-ended strategic question
claude-agent ceo "What should our top priority be for the next 90 days?"

# Specific skill
claude-agent ceo --skill production-readiness-analysis

# Quick command
claude-command ceo:quick-health-check
```

### Agent Detection Mode

When the CEO agent starts, it automatically checks for companion agents. You'll see one of:

```
✅ All 4 agents available. Full orchestration active.
```

```
⚠️ 2/4 agents found. Proceeding with financial-advisor, product-manager.
   Missing: tax-advisor, ai-specialist
   Install: /plugin install tax-advisor@jontoio-claude-agents
```

```
⚠️ CEO Agent Alert: No marketplace agents detected. General advice only.
   Install agents from https://github.com/jontoIO/claude-agents
```

---

## Marketplace Structure

```
plugins/ceo/
├── .claude-plugin/
│   └── plugin.json                   # Plugin manifest
├── agents/
│   └── ceo.md                        # CEO agent definition
├── skills/
│   ├── strategic-assessment/         # Full situation analysis
│   ├── production-readiness-analysis/ # Launch decision framework
│   ├── opportunity-analysis/         # Business opportunity evaluation
│   ├── executive-briefing/           # Multi-agent executive summary
│   └── company-roadmap-planning/     # Cross-functional roadmap
├── commands/
│   ├── quick-health-check.md         # 2-3 min health snapshot
│   ├── production-go-nogo.md         # Quick launch verdict
│   ├── opportunity-scan.md           # Quick opportunity score
│   └── weekly-ceo-briefing.md        # Weekly executive summary
├── examples/
│   └── production-launch-decision.md # Full orchestration walkthrough
├── README.md
└── CHANGELOG.md
```

---

## Integration with Other Plugins

The CEO agent is designed to be the entry point for complex questions that span multiple domains. Use it when:

- A question is too complex for a single specialized agent
- You need a unified recommendation across financial, product, legal, and technical dimensions
- You want cross-domain conflicts surfaced and resolved
- You need executive-level output (board-ready, investor-ready, decision-focused)

For single-domain deep dives, invoke the specialist agent directly:

```bash
# Financial deep dive
/financial-advisor:cost-estimation

# Product deep dive
/product-manager:competitive-intelligence

# Tax deep dive
/tax-advisor:vat-analysis

# Technical deep dive
/ai-specialist:token-optimization-audit
```

---

## Disclaimer

The CEO agent provides strategic guidance for planning purposes only. It is not a substitute for professional legal, financial, or tax advice. All domain analyses are estimates based on available data and agent outputs. Validate all major financial and legal decisions with qualified professionals before acting.

---

## Version History

- **1.0.0** (February 2026): Initial release — multi-agent orchestration, 5 skills, 4 commands, graceful degradation with 0-4 companion agents

## Installation

```bash
/plugin install ceo@jontoio-claude-agents
```

## License

MIT — see [LICENSE](../../LICENSE)
