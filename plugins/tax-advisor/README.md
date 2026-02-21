# Tax Advisor Plugin

An EU tax analysis plugin for software founders, freelancers, and SaaS teams. Scans repositories for financial signals, fetches live rates from official tax authority websites, and produces tax estimates, VAT/IVA analysis, deduction reports, and compliance calendars.

## Overview

The Tax Advisor Plugin helps software businesses understand and plan their EU tax obligations by:

- **Scanning repositories** automatically for revenue and cost signals (Stripe, AWS, Sentry, etc.)
- **Fetching live rates** from 8 official EU government tax authority websites via WebFetch
- **Conducting structured interviews** to collect financial data not visible in code
- **Producing tax estimates** with three scenarios (conservative/realistic/optimistic)
- **Classifying VAT obligations** including OSS threshold assessment for cross-border EU sales
- **Generating compliance calendars** with exact deadlines, amounts, and penalty schedules

**Default country**: Spain. All 8 supported EU countries work with the same skill set.

## Supported Countries

| Country | Authority | Website | Corporate Tax | VAT |
|---------|-----------|---------|--------------|-----|
| Spain (ES) | AEAT | aeat.es | IS 25% / 15% new co | IVA 21% |
| Germany (DE) | BMF | bundesfinanzministerium.de | ~30% effective | USt 19% |
| France (FR) | DGFiP | impots.gouv.fr | IS 25% | TVA 20% |
| Italy (IT) | AdE | agenziaentrate.gov.it | IRES 24% + IRAP 3.9% | IVA 22% |
| Netherlands (NL) | BD | belastingdienst.nl | VPB 19%/25.8% | BTW 21% |
| Portugal (PT) | AT | portaldasfinancas.gov.pt | IRC 21%/17% small | IVA 23% |
| Poland (PL) | KAS | podatki.gov.pl | CIT 9%/19% | VAT 23% |
| Ireland (IE) | Revenue | revenue.ie | CT 12.5% trading | VAT 23% |

## Project Types Supported

- B2B SaaS applications
- B2C SaaS and digital products
- Freelance software development
- API services and microSaaS
- Digital agencies
- Open source projects with commercial sponsorship or consulting revenue
- Software consultancies

## Key Features

### 1. Repository Financial Signal Scanning
Automatically detects expense signals from:
- Cloud infrastructure configs (AWS, GCP, Azure environment variables)
- Payment processing integrations (Stripe, PayPal, Paddle)
- Monitoring tools (Sentry, Datadog, New Relic)
- Communication services (SendGrid, Mailgun)
- CI/CD configurations (GitHub Actions, CircleCI)
- Dependency files (package.json, requirements.txt, go.mod)

### 2. Live Tax Rate Retrieval
Fetches current rates from official government sources before every analysis. No hardcoded rates that become stale. Always cites the source URL and fetch date.

### 3. Structured Financial Interview
When data is not visible in code, asks up to 8 numbered questions covering:
- Gross revenue and geography split
- B2B vs B2C breakdown and VAT number status
- Employee and contractor costs
- Office, training, and hardware expenses
- Prior year losses for carryforward

### 4. EU VAT Classification
Applies current EU VAT rules:
- Domestic B2B/B2C: charge standard domestic rate
- EU B2B with valid VAT number: reverse-charge (0% + required invoice text)
- EU B2C digital services < €10,000: seller's country rate
- EU B2C digital services > €10,000: OSS required, buyer's country rate
- Non-EU: zero-rated

### 5. Compliance Calendar
Month-by-month calendar for the next 12 months covering:
- VAT/IVA quarterly filings (Modelo 303, Voranmeldung, CA3, VAT3, etc.)
- Corporate tax advance payments and annual return
- Withholding summaries (Modelo 190, Modelo 347)
- Penalty schedule for late filing (Spain: 5%/10%/15%/20% surcharges)
- Monthly cash reserve plan

## Usage

### Standard Workflow

```bash
# Step 1: Load country context with live rates
/tax-advisor:tax-country-setup ES

# Step 2: Auto-scan repo for deduction signals
/tax-advisor:deductions-scan

# Step 3: Full VAT analysis and OSS assessment
/tax-advisor:vat-analysis

# Step 4: Complete tax estimation (IS/CT + VAT + IRPF if autónomo)
/tax-advisor:tax-estimation

# Step 5: 12-month compliance calendar
/tax-advisor:compliance-calendar
```

### Quick Estimate (2 minutes)

```bash
# Rapid ballpark estimate without repo scan
/tax-advisor:quick-tax-estimate 85000 --country ES --structure sl
/tax-advisor:quick-tax-estimate 45000 --country ES --structure autónomo --new-company
/tax-advisor:quick-tax-estimate 120000 --country IE --structure ltd
```

### Country Comparison (for incorporation decisions)

```bash
# Compare Spain vs Ireland
/tax-advisor:tax-country-setup ES --compare IE

# Compare Netherlands vs Germany
/tax-advisor:tax-country-setup NL --compare DE
```

### Deduction Discovery Only

```bash
# Scan repo for deductible expense signals
/tax-advisor:deductions-scan

# Full deduction analysis with documentation requirements
/tax-advisor:deduction-analysis
```

## Components

| Type | Name | Description | Time |
|------|------|-------------|------|
| Agent | `tax-advisor` | Main EU tax analysis agent with country + structure setup | — |
| Skill | `country-tax-rules` | Fetch live rates from official authority + country comparison | 5-10 min |
| Skill | `deduction-analysis` | Repo scan + interview + deduction table with documentation requirements | 20-30 min |
| Skill | `vat-analysis` | VAT classification, OSS assessment, quarterly calendar | 20-25 min |
| Skill | `tax-estimation` | Full IS/CT + VAT/IVA + IRPF calculation with 3 scenarios | 30-40 min |
| Skill | `compliance-calendar` | Month-by-month filing calendar with deadlines, amounts, penalties | 15-20 min |
| Command | `tax-country-setup` | Quick country card with optional comparison | 2-3 min |
| Command | `deductions-scan` | Automated repo scan for deductible expense signals | 3-5 min |
| Command | `quick-tax-estimate` | Rapid ballpark estimate from revenue + country + structure | 2 min |

## Installation

```bash
/plugin install tax-advisor@jontoio-claude-agents
```

## Example

See [examples/saas-eu-startup.md](examples/saas-eu-startup.md) for a complete walkthrough using NebulaPay SL — a Spanish B2B SaaS with €95,000 revenue, German contractor, and AWS + Stripe + Sentry in the repo.

Key findings from the example:
- IS reduced from €23,750 (25%) to **€4,985** (15% new-company rate + deductions)
- Reverse-charge applies to 35% of revenue (EU B2B) — no IVA collected on those sales
- Modelo 347 required for German contractor (> €3,005 threshold)
- Total tax €14,393 (effective rate 15.15% of revenue)
- Monthly cash reserve: €1,199/month

## Integration with Financial Advisor Plugin

The Tax Advisor Plugin complements the Financial Advisor Plugin:

| Financial Advisor | Tax Advisor |
|-------------------|-------------|
| Cost estimation (infrastructure, APIs) | Tax deduction analysis (what's deductible) |
| Revenue modeling | VAT on revenue (what VAT to charge) |
| ROI analysis | After-tax ROI (realistic profitability) |
| Financial risk assessment | Tax compliance risk (penalties, OSS) |

Typical workflow combining both plugins:
1. Run `financial-advisor:cost-estimation` to understand total costs
2. Run `tax-advisor:deductions-scan` to identify deductible portion of those costs
3. Run `tax-advisor:tax-estimation` to calculate after-tax profit

## Limitations

**This plugin does NOT provide**:
- Professional tax advice — always consult a licensed gestor/asesor fiscal before filing
- R&D tax credit calculations (France CIR, Ireland R&D Credit, Spain I+D+i) — flag only, not calculated
- Social security precise calculations — approximations only, varies by income and country
- Multi-jurisdiction analysis for companies with operations in multiple EU countries simultaneously
- Country-specific municipality tax variations (Germany Gewerbesteuer varies by city)
- Historical analysis — designed for current/upcoming fiscal year planning
- Legal opinions on structuring or optimization strategies

**Rate accuracy**:
- Rates are fetched from official sources at time of analysis — always current
- Legislative changes between fetch and filing may affect rates
- Always verify rates with your gestor before filing

## Disclaimer

This plugin is an estimation tool for planning purposes only. Tax laws change frequently and individual circumstances vary significantly. The plugin does not constitute tax advice. Always consult a licensed tax advisor (gestor/asesor fiscal) before filing any tax returns or making financial decisions based on this analysis.

## License

MIT — See repository root LICENSE file.
