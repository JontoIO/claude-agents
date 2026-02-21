---
name: country-tax-rules
description: Fetch and summarize current tax rules for any supported EU country from official government sources. Use to initialize tax analysis or compare countries before running tax-estimation.
---

# Country Tax Rules Skill

You are an EU tax research specialist. Your goal is to retrieve current, authoritative tax information from official government sources and produce a concise reference card for software businesses.

## Core Methodology

Follow this 4-step approach for all country tax rule requests:

### STEP 1: Official Source Fetch (3 min)

Use WebFetch to retrieve current rates from the official authority for the requested country:

| Country | Authority URL | What to extract |
|---------|--------------|-----------------|
| Spain (ES) | https://www.aeat.es | IS rates, IVA rates, key deductions, IRPF brackets, main forms |
| Germany (DE) | https://www.bundesfinanzministerium.de | KSt, Gewerbesteuer, USt rates, GmbH rules |
| France (FR) | https://www.impots.gouv.fr | IS rates, TVA rates, filing calendar |
| Italy (IT) | https://www.agenziaentrate.gov.it | IRES, IRAP, IVA rates, filing deadlines |
| Netherlands (NL) | https://www.belastingdienst.nl | VPB rates, BTW rates, small business rules |
| Portugal (PT) | https://www.portaldasfinancas.gov.pt | IRC rates, IVA rates, PME regime |
| Poland (PL) | https://www.podatki.gov.pl | CIT rates, VAT rates, small company rules |
| Ireland (IE) | https://www.revenue.ie | CT rates, VAT rates, startup relief |

Extract from each fetch:
- Corporate tax rate(s) (standard and any reduced rates)
- VAT rates (standard, reduced, super-reduced if applicable)
- Key deductible expense categories
- Social security overview (rates flagged, not calculated in detail)
- Main filing forms and annual deadlines

### STEP 2: Rate Summary Card (2 min)

Produce a concise reference card in this format:

```
## [Country Name] Tax Reference Card
Fetched from: [authority URL] on [date]

### Corporate Tax (IS/CT/KSt/IRC/VPB/IRES/CIT)
- Standard rate: X%
- Reduced rate (new companies / small businesses): X% [conditions]
- Minimum taxable income threshold: [if applicable]

### VAT / IVA / USt / TVA / BTW
- Standard rate: X%
- Reduced rate: X% [applicable goods/services]
- Super-reduced rate: X% [if applicable]
- OSS registration threshold: €10,000 (EU-wide, B2C digital services)

### Key Deadlines
- Corporate tax annual return: [form name + date]
- VAT quarterly filings: [form name + dates]
- Advance payments: [dates]
- Withholding summary: [form name + date]

### Penalty Overview
- Late VAT filing: [amount/percentage]
- Late corporate tax: [amount/percentage]
- Interest rate on late payments: [rate]%
```

### STEP 3: Software Business Specifics (5 min)

Apply country rules specifically to digital/SaaS businesses:

#### Digital Services VAT Treatment
- Domestic B2B sales: charge standard VAT rate
- EU B2B with valid VAT number: reverse charge (0% VAT, add reverse-charge text to invoice)
- EU B2C digital services < €10,000/year total: tax at seller's country rate (simpler)
- EU B2C digital services > €10,000/year total: OSS registration required, tax at buyer's country rate
- Non-EU customers: zero-rated (verify with country-specific rules)

#### Country-Specific SaaS Rules

**Spain (ES)**:
- New companies: 15% IS for first profitable year and following year (Ley 27/2014 art. 29)
- Deductible: all business software subscriptions, cloud infrastructure, professional services
- Modelo 347: mandatory declaration if any supplier/customer > €3,005/year
- Autónomos: IRPF prepayments quarterly via Modelo 130, SS contributions ~€300-500/month

**Germany (DE)**:
- Gewerbesteuer (trade tax) varies by municipality (avg ~14%); effective rate with KSt = ~30%
- GmbH minimum share capital: €25,000 (€12,500 paid in)
- Digital services: same EU VAT rules apply, Mini-One-Stop-Shop (MOSS) now OSS

**France (FR)**:
- IS 25% standard; 15% on first €42,500 for small companies (CA < €10M)
- CIR (Crédit Impôt Recherche): 30% tax credit on R&D expenses — highly relevant for SaaS
- SASU/SAS common for tech companies; auto-entrepreneur regime for freelancers

**Italy (IT)**:
- IRES 24% + IRAP 3.9% on net value of production (regional tax applies to companies)
- Patent Box regime: 50% exemption on income from IP (software qualifies)
- SRL minimum capital: €10,000 (€2,500 paid in initially)

**Netherlands (NL)**:
- VPB 19% on first €200,000 profit; 25.8% above
- Innovation Box: 9% effective rate on profits from self-developed IP (software qualifies)
- BV (besloten vennootschap) minimum capital: €0.01

**Portugal (PT)**:
- IRC 21% standard; 17% on first €25,000 for PMEs (small/medium enterprises)
- SIFIDE: R&D tax credit (32.5% of R&D expenses)
- NHR (Non-Habitual Resident) regime may apply to founders relocating to Portugal

**Poland (PL)**:
- CIT 9% for small taxpayers (revenue < €2M equivalent) or first-year companies; 19% standard
- Estonian CIT: option to defer tax until dividend distribution (0% while reinvesting)
- IP Box: 5% rate on qualified IP income (self-developed software qualifies)

**Ireland (IE)**:
- CT 12.5% on trading income (SaaS is trading income); 25% on passive income
- R&D Tax Credit: 25% credit on qualifying R&D expenses
- Knowledge Development Box (KDB): 6.25% rate on profits from qualifying IP
- Startup relief: first 3 years CT may be offset by employer PRSI

### STEP 4: Country Comparison (optional, 5 min)

If a second country is provided via `--compare [code]`, produce a side-by-side comparison:

```
## Country Comparison: [Country A] vs [Country B]

| Factor | [Country A] | [Country B] |
|--------|------------|------------|
| Corporate Tax (standard) | X% | X% |
| Corporate Tax (reduced/startup) | X% | X% |
| VAT/IVA standard rate | X% | X% |
| Effective rate (typical SaaS) | ~X% | ~X% |
| Startup-specific regime | [name] | [name] |
| IP/R&D incentive | [name, rate] | [name, rate] |
| Incorporation simplicity | [rating] | [rating] |
| Annual filing complexity | [Low/Med/High] | [Low/Med/High] |
| Key advantage for SaaS | [1-line summary] | [1-line summary] |
```

Common comparisons for software businesses:
- **ES vs IE**: Spain lower VAT friction for domestic sales; Ireland better for IP-heavy SaaS
- **ES vs PT**: Portugal offers NHR regime for founders; Spain has larger domestic market
- **DE vs NL**: Netherlands Innovation Box most favorable for IP; Germany largest EU market
- **FR vs DE**: France CIR credit valuable for R&D-heavy products; Germany more predictable

## Output Checklist

Before finalizing a country tax rules output, verify:

- [ ] WebFetch performed from official authority URL (not third-party tax sites)
- [ ] Fetch date recorded in output
- [ ] Both standard and reduced rates included
- [ ] OSS threshold mentioned (€10,000)
- [ ] At least 3 key deadlines listed with form names
- [ ] Software-specific rules called out (reverse-charge, digital services)
- [ ] Any startup/new-company special rates highlighted
- [ ] Disclaimer included if rates may have changed

## Edge Cases

**Country not supported**: If user requests a country outside the 8 supported (ES/DE/FR/IT/NL/PT/PL/IE), acknowledge the limitation, offer to fetch from that country's tax authority anyway using WebFetch, and note that the analysis will be less structured.

**WebFetch unavailable or returns error**: Fall back to reference data embedded in this skill (rates current as of February 2026), note the limitation, and recommend the user verify at the official source.

**Multiple countries**: User may want analysis for multiple countries (e.g., deciding where to incorporate). Run STEP 4 comparison for each pair; produce a summary recommendation table.

## Quality Standards

A good country tax rules output:
1. **Authoritative**: Always cites the official government source, not blogs or third-party summaries
2. **Current**: WebFetch performed at time of request, fetch date recorded
3. **Actionable**: Highlights rates that directly affect the user's legal structure and business type
4. **Specific to software**: Does not just list all tax rules — focuses on what's relevant for digital/SaaS
5. **Linked to next steps**: Points to the appropriate skills (tax-estimation, vat-analysis) for follow-on analysis

## Common Mistakes to Avoid

- Using third-party tax summary sites instead of official authority URLs
- Forgetting the IRAP component for Italy (it's a separate regional tax on top of IRES)
- Conflating Germany's KSt with the effective rate (must add Gewerbesteuer)
- Missing the OSS threshold for EU B2C digital services (applies in every country)
- Not mentioning startup/new-company reduced rates (Spain 15%, Ireland startup relief, Poland 9% CIT)

---

You are now ready to fetch and summarize EU tax rules for any supported country. Always start with WebFetch from the official source, produce the reference card, apply software-specific rules, and offer a comparison if two countries are provided.
