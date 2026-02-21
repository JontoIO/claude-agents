# Claude Agents Plugin Marketplace

A curated collection of Claude AI plugins for financial analysis, product management, and AI optimization.

## 📖 Overview

This repository is a **Claude Code plugin marketplace** that provides professional-grade plugins to enhance Claude's capabilities. Each plugin is a self-contained package with agents, skills, and commands for specific use cases.

## 🚀 Quick Start

### Add This Marketplace

```bash
# Add the marketplace to Claude Code
/plugin marketplace add jontoIO/claude-agents

# Verify the marketplace is available
/plugin
```

### Install a Plugin

```bash
# Install the financial advisor plugin
/plugin install financial-advisor@jontoio-claude-agents

# Use the plugin's features
/financial-advisor:quick-cost-estimate
/financial-advisor:cost-estimation
/agents  # See the financial-advisor agent
```

## 📦 Available Plugins

### Financial Advisor

**Version**: 1.0.0

A comprehensive financial analysis plugin for software projects, providing cost estimation, revenue modeling, risk assessment, and ROI analysis.

**Features**:
- Cost estimation for APIs, infrastructure, and development
- Revenue modeling and pricing strategies
- Financial risk identification and mitigation
- ROI calculations and break-even analysis
- Compliance guidance (GDPR, HIPAA, SOC2, PCI-DSS)

**Components**:
- **Agent**: `financial-advisor` - Specialized financial planning agent
- **Skills**:
  - `cost-estimation` - Systematic 5-step cost analysis
  - `monetization-planning` - Revenue strategies and pricing models
  - `financial-risk-assessment` - Risk identification and compliance
  - `roi-analysis` - Return on investment calculations
- **Commands**:
  - `quick-cost-estimate` - Rapid cost estimates (±30-40% accuracy)

**Installation**:
```bash
/plugin install financial-advisor@jontoio-claude-agents
```

**Documentation**: [Plugin README](./plugins/financial-advisor/README.md)

---

### Product Manager

**Version**: 1.0.0

A comprehensive product management plugin that provides product strategy, competitive analysis, persona definition, improvement proposals, and changelog creation capabilities for any software product.

**Features**:
- Product evolution analysis with prioritized roadmaps
- Competitive intelligence with feature matrices
- Evidence-based user personas using jobs-to-be-done
- Prioritized improvement proposals with RICE scoring
- Compelling changelogs optimized for different audiences

**Components**:
- **Agent**: `product-manager` - Strategic product management specialist
- **Skills**:
  - `product-evolution-analysis` - 7-step product assessment and roadmap
  - `competitive-intelligence` - 7-step competitive research and positioning
  - `persona-definition` - 6-step evidence-based persona creation
  - `improvement-proposals` - 6-step prioritized feature proposals
  - `changelog-creation` - 5-step user-facing changelog generation
- **Commands**:
  - `quick-competitive-scan` - 5-10 min rapid competitor overview
  - `quick-changelog` - 3-5 min user-facing changelog from commits
  - `persona-quick-reference` - 5 min basic persona profile
  - `feature-impact-estimate` - 3-5 min RICE score and go/no-go

**Installation**:
```bash
/plugin install product-manager@jontoio-claude-agents
```

**Documentation**: [Plugin README](./plugins/product-manager/README.md)

---

### AI Specialist

**Version**: 1.0.0

A proactive AI optimization plugin that monitors Claude sessions, optimizes instructions, improves memory efficiency, designs test strategies, and reduces token usage for Claude-powered projects.

**Features**:
- Claude instructions optimization (20-40% token reduction)
- Memory efficiency analysis for better context retention
- Test strategy design ensuring 100% test coverage
- Prompt enhancement for clarity and efficiency
- Token optimization audits with cost savings analysis
- Proactive monitoring suggesting improvements at optimal moments

**Components**:
- **Agent**: `ai-specialist` - Proactive AI optimization specialist
- **Skills**:
  - `claude-instructions-optimization` - 7-step CLAUDE.md optimization
  - `memory-efficiency-analysis` - 6-step MEMORY.md optimization
  - `test-strategy-design` - 5-step comprehensive test planning
  - `prompt-enhancement` - 6-step prompt clarity and efficiency
  - `token-optimization-audit` - 7-step token analysis and roadmap
- **Commands**:
  - `quick-instruction-audit` - 5-7 min CLAUDE.md review with top 3 issues
  - `quick-test-plan` - 3-5 min test strategy addition
  - `token-usage-snapshot` - 2-3 min token overview and opportunities

**Installation**:
```bash
/plugin install ai-specialist@jontoio-claude-agents
```

**Documentation**: [Plugin README](./plugins/ai-specialist/README.md)

---

### Tax Advisor

**Version**: 1.0.0

An EU tax analysis plugin for software founders, freelancers, and SaaS teams. Scans repositories for financial signals, fetches live rates from official tax authority websites, and produces tax estimates, VAT/IVA analysis, deduction reports, and compliance calendars for 8 EU countries.

**Features**:
- Automatic repository scanning for revenue/cost signals (Stripe, AWS, Sentry, SendGrid, etc.)
- Live tax rate retrieval from 8 official EU government websites via WebFetch
- EU VAT/IVA classification with reverse-charge, OSS threshold assessment, and quarterly calendar
- Corporate tax estimation (IS/CT/KSt/IRES/VPB/IRC/CIT) with three scenarios
- Deduction discovery with documentation requirements and Modelo 347 flagging
- Month-by-month compliance calendar with deadlines, amounts, and penalty schedule

**Components**:
- **Agent**: `tax-advisor` - EU tax analysis specialist with live-rate fetching
- **Skills**:
  - `country-tax-rules` - Fetch live rates from official authority + country comparison
  - `deduction-analysis` - Repo scan + interview + documented deduction table
  - `vat-analysis` - EU VAT classification, OSS assessment, quarterly obligations
  - `tax-estimation` - Full IS/CT + VAT/IVA + IRPF calculation with 3 scenarios
  - `compliance-calendar` - Month-by-month filing calendar with deadlines and penalties
- **Commands**:
  - `tax-country-setup` - Country reference card with optional comparison (2-3 min)
  - `deductions-scan` - Automated repo scan for deductible expense signals (3-5 min)
  - `quick-tax-estimate` - Rapid ballpark estimate from revenue + country + structure (2 min)

**Supported Countries**: Spain, Germany, France, Italy, Netherlands, Portugal, Poland, Ireland

**Installation**:
```bash
/plugin install tax-advisor@jontoio-claude-agents
```

**Documentation**: [Plugin README](./plugins/tax-advisor/README.md)

## 📁 Marketplace Structure

```
claude-agents/                          # Marketplace root
├── .claude-plugin/
│   └── marketplace.json                # Marketplace manifest
├── plugins/
│   ├── financial-advisor/              # Financial advisor plugin
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json             # Plugin manifest
│   │   ├── agents/
│   │   │   └── financial-advisor.md    # Agent definition
│   │   ├── skills/                     # 4 financial skills
│   │   ├── commands/                   # Quick cost estimate
│   │   ├── examples/                   # SaaS startup example
│   │   ├── README.md                   # Plugin documentation
│   │   └── CHANGELOG.md                # Version history
│   ├── product-manager/                # Product manager plugin
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json
│   │   ├── agents/
│   │   │   └── product-manager.md
│   │   ├── skills/                     # 5 product skills
│   │   ├── commands/                   # 4 quick commands
│   │   ├── examples/                   # Product examples
│   │   ├── README.md
│   │   └── CHANGELOG.md
│   └── ai-specialist/                  # AI specialist plugin
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── agents/
│       │   └── ai-specialist.md
│       ├── skills/                     # 5 optimization skills
│       ├── commands/                   # 3 quick commands
│       ├── examples/                   # Optimization examples
│       ├── README.md
│       └── CHANGELOG.md
├── docs/
│   ├── creating-plugins.md             # Plugin development guide
│   └── marketplace-setup.md            # Marketplace usage guide
└── README.md                           # This file
```

## 🔧 Usage Examples

### Quick Cost Estimate

```bash
# Get a rapid cost estimate for a feature
/financial-advisor:quick-cost-estimate Add AI-powered content summarization feature

# With parameters for more accuracy
/financial-advisor:quick-cost-estimate Add real-time collaboration --users 5000 --team "3 senior devs, 1 DevOps" --timeline "3 months"
```

### Full Cost Estimation

```bash
# Invoke the cost estimation skill
/financial-advisor:cost-estimation

# The agent will:
# 1. Gather project data (read files, ask questions)
# 2. Categorize costs (APIs, infrastructure, development)
# 3. Model usage scenarios (low/medium/high)
# 4. Calculate detailed costs
# 5. Provide optimization recommendations
```

### Financial Risk Assessment

```bash
# Assess financial risks for your project
/financial-advisor:financial-risk-assessment

# The agent will:
# 1. Identify regulatory compliance requirements
# 2. Analyze cost overrun risks
# 3. Evaluate integration dependencies
# 4. Review revenue model sustainability
# 5. Provide mitigation strategies
```

### ROI Analysis

```bash
# Calculate return on investment for a feature
/financial-advisor:roi-analysis

# The agent will:
# 1. Calculate investment costs
# 2. Estimate returns and savings
# 3. Determine break-even point
# 4. Model best/realistic/worst scenarios
# 5. Provide go/no-go recommendation
```

## 🤝 Contributing

We welcome contributions to this marketplace! You can:

- **Submit new plugins** to expand the marketplace
- **Improve existing plugins** with enhancements and bug fixes
- **Report issues** or suggest improvements

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines on:
- Creating new plugins
- Plugin structure requirements
- Testing plugins locally
- Submitting pull requests

## 📚 Documentation

- [Plugin Development Guide](./docs/creating-plugins.md) - How to create new plugins
- [Marketplace Setup Guide](./docs/marketplace-setup.md) - How to use this marketplace
- [Financial Advisor Plugin](./plugins/financial-advisor/README.md) - Financial analysis documentation
- [Product Manager Plugin](./plugins/product-manager/README.md) - Product management documentation
- [AI Specialist Plugin](./plugins/ai-specialist/README.md) - AI optimization documentation

## 🔗 Resources

- [Claude Code Documentation](https://github.com/anthropics/claude-code)
- [Claude AI Documentation](https://docs.anthropic.com/claude/docs)
- [Model Context Protocol](https://modelcontextprotocol.io/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## 🌟 Marketplace Information

- **Name**: jontoio-claude-agents
- **Owner**: JontoIO
- **Version**: 1.0.0
- **Plugins**: 3 available (Financial Advisor, Product Manager, AI Specialist)

## 🔮 Future Plugins

We're planning to add more plugins in the future:
- Code review and quality analysis
- Documentation generation
- API design and documentation
- Security and vulnerability analysis
- DevOps and infrastructure optimization

Stay tuned for updates!

---

**Note**: This is a curated marketplace. All plugins are tested and documented. Always review plugin documentation before installation.
