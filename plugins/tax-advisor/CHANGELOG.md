# Changelog

All notable changes to the Tax Advisor plugin are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] — 2026-02-21

### Added

#### Plugin Infrastructure
- `.claude-plugin/plugin.json` — Plugin manifest with metadata, keywords, and author information
- `agents/tax-advisor.md` — Main agent definition with startup behavior, capabilities, supported countries table, and 7-step approach
- `README.md` — Full plugin documentation with usage examples, component table, and limitations
- `CHANGELOG.md` — This file

#### Skills (5 total)
- `skills/country-tax-rules/SKILL.md` — Fetches live rates from official EU tax authority websites; produces country reference cards and side-by-side country comparisons; covers software-business-specific rules (reverse-charge, OSS, IP regimes) for all 8 countries
- `skills/deduction-analysis/SKILL.md` — Systematic deduction discovery from repo configs and dependencies; 5-category classification system; documentation requirements per deduction; gap interview for non-repo expenses; Modelo 347 flagging for Spain
- `skills/vat-analysis/SKILL.md` — EU VAT/IVA classification for all revenue streams; reverse-charge rule matrix with required invoice text in all 8 languages; OSS threshold assessment (€10,000); quarterly input VAT credit calculation; country-specific quarterly filing calendars
- `skills/tax-estimation/SKILL.md` — Full annual tax liability estimation covering IS/CT/KSt/IRES/VPB/IRC/CIT + VAT/IVA + IRPF (for autónomos); 6-step methodology; 3-scenario output (conservative/realistic/optimistic); formula-transparent calculations; sample NebulaPay SL output included
- `skills/compliance-calendar/SKILL.md` — Month-by-month filing calendar for all 8 countries; complete obligation inventory (VAT quarterly, IS advance payments, annual returns, withholding summaries, social security); penalty schedule for late filing; cash reserve plan; 30-day and 90-day action horizons

#### Commands (3 total)
- `commands/tax-country-setup.md` — Fetches live rates from official authority; produces reference card in 2-3 minutes; optional `--compare` flag for side-by-side country comparison; saves country context for session
- `commands/deductions-scan.md` — Automated 5-phase repo scan (env files, package dependencies, infrastructure configs, CI/CD, source code); produces preliminary deduction table with confidence levels (HIGH/MEDIUM/LOW); no user input required
- `commands/quick-tax-estimate.md` — Rapid ballpark estimate from revenue + country + structure flags; ±30-35% accuracy; supports `--new-company`, `--b2b-eu-pct`, `--expenses` flags; covers IS/CT, VAT/IVA, and IRPF (Spain autónomo)

#### Examples
- `examples/saas-eu-startup.md` — Complete walkthrough: NebulaPay SL (Spain, B2B SaaS, €95,000 revenue, first profitable year, German contractor, AWS + Stripe + Sentry); demonstrates all 5 skills; documents 5 key teaching moments (new company IS rate, reverse-charge, Modelo 347, home office complexity, AWS invoice VAT)

### Supported Countries
- 🇪🇸 Spain (ES) — AEAT — IS 25%/15% new co, IVA 21%
- 🇩🇪 Germany (DE) — BMF — ~30% effective (KSt + GewSt), USt 19%
- 🇫🇷 France (FR) — DGFiP — IS 25%, TVA 20%
- 🇮🇹 Italy (IT) — AdE — IRES 24% + IRAP 3.9%, IVA 22%
- 🇳🇱 Netherlands (NL) — BD — VPB 19%/25.8%, BTW 21%
- 🇵🇹 Portugal (PT) — AT — IRC 21%/17% small, IVA 23%
- 🇵🇱 Poland (PL) — KAS — CIT 9%/19%, VAT 23%
- 🇮🇪 Ireland (IE) — Revenue — CT 12.5% trading, VAT 23%

### Key Features Delivered
- Automatic repository scanning for financial signals (8 service categories, 5 scan phases)
- Live rate retrieval from official government sources via WebFetch (no hardcoded rates)
- EU VAT rule matrix with reverse-charge invoice text in all 8 country languages
- OSS threshold assessment (€10,000 EU B2C digital services)
- Three-scenario tax modeling with formula transparency
- Month-by-month compliance calendar with penalty schedule
- Cash reserve planning (monthly set-aside recommendations)
- Integration guide with Financial Advisor plugin

---

## Future Roadmap

### [1.1.0] — Planned
- R&D tax credit calculations (France CIR 30%, Ireland 25%, Spain I+D+i)
- IP Box regime analysis (Netherlands Innovation Box 9%, Ireland KDB 6.25%, Poland 5%)
- Founder salary optimization (autónomo vs SL salary + dividend comparison for Spain)
- Expanded country support: Belgium, Sweden, Denmark

### [1.2.0] — Planned
- Multi-year projections (carryforward losses, growth scenarios)
- Employee equity (ESOP/phantom shares) tax treatment per country
- Double taxation treaty reference (Spain-Germany, Spain-UK, etc.)
- Direct integration with financial-advisor plugin for combined cost + tax analysis

### [2.0.0] — Future
- Real-time AEAT / tax authority API integration (when available)
- Automatic Modelo 303 / Modelo 200 data pre-population
- Multi-jurisdiction analysis for companies with EU permanent establishments
- VAT number validation via EU VIES API
