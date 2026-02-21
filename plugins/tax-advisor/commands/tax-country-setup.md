# Tax Country Setup Command

Fetches live tax rates from the official EU tax authority website for a given country and produces a concise reference card. Optionally compares two countries side by side.

## Purpose

Initialize tax analysis with current, authoritative rates before running any tax estimation or VAT analysis. This command ensures all subsequent analysis uses rates from official government sources, not outdated third-party summaries.

## When to Use

**Use tax-country-setup when**:
- Starting any tax analysis for a new country
- Verifying that rates have not changed since last analysis
- Deciding between two EU countries for incorporation
- Preparing for a conversation with a gestor/tax advisor and need a quick reference
- After any major legislative announcement that may affect tax rates

**Use full country-tax-rules skill when**:
- You need software-specific rules (digital services VAT, IP regimes)
- You want a full comparison with actionable incorporation advice
- You need all filing deadlines and form names for a compliance calendar

## Command Format

```bash
/tax-country-setup [country-code] [--compare country-code]
```

### Parameters

```
[country-code]        Required. One of: ES, DE, FR, IT, NL, PT, PL, IE
--compare [code]      Optional. Second country code for side-by-side comparison
```

## Examples

### Example 1: Single Country Setup

```bash
/tax-country-setup ES
```

**Expected Output**:
```
## Spain (ES) Tax Reference Card
Source: aeat.es | Fetched: 2026-02-21

### Corporate Tax (Impuesto de Sociedades — IS)
- Standard rate: 25%
- New company rate: 15% (first two profitable fiscal years)
- Condition for new company rate: First year with positive taxable base

### VAT (IVA — Impuesto sobre el Valor Añadido)
- Standard rate: 21%
- Reduced rate: 10% (food, transport, hospitality)
- Super-reduced rate: 4% (basic necessities, books, medicine)
- OSS registration: via AEAT sede.aeat.gob.es

### IRPF (Personal Income Tax — for autónomos)
- Brackets: 19% (0-€12,450) / 24% (€12,451-€20,200) / 30% (€20,201-€35,200) /
            37% (€35,201-€60,000) / 45% (€60,001-€300,000) / 47% (>€300,000)
- Quarterly prepayment: Modelo 130 (20% of net quarterly income)

### Social Security (approx.)
- Autónomo (self-employed): ~€300-500/month (Cuota RETA, income-based since 2023)
- Employee (employer contribution): ~29-30% of gross salary
- Employee (employee contribution): ~6.35% of gross salary

### Key Filing Deadlines
- Modelo 303 IVA Q4: January 30
- Modelo 190 IRPF summary: January 31
- Modelo 347 third-party operations: March 31
- Modelo 303 IVA Q1 + Modelo 111 IRPF withholdings: April 20
- Modelo 303 IVA Q2 + Modelo 111: July 20
- Modelo 200 IS annual return: July 25
- Modelo 303 IVA Q3 + Modelo 111 + Modelo 202 IS advance: October 20
- Modelo 202 IS advance (3rd): December 20

### Late Payment Interest Rate
- 4.0625% annual (2025/2026)

This reference card is ready. Run `/tax-advisor:tax-estimation` for a full analysis.
```

### Example 2: Country Comparison

```bash
/tax-country-setup ES --compare IE
```

**Expected Output**:
```
## Tax Comparison: Spain (ES) vs Ireland (IE)
Fetched from: aeat.es + revenue.ie | Date: 2026-02-21

| Factor | Spain | Ireland |
|--------|-------|---------|
| Corporate Tax (standard) | 25% | 12.5% (trading) |
| Corporate Tax (startup/reduced) | 15% (first 2 profitable years) | Startup relief (offset by employer PRSI, first 3 years) |
| VAT standard rate | 21% | 23% |
| Effective corporate rate (typical SaaS) | ~18-22% with deductions | ~12.5% (trading income) |
| IP/R&D regime | None specific to SaaS | Knowledge Dev Box 6.25% + R&D credit 25% |
| EU market access | Yes (Schengen + Eurozone) | Yes (common law, English-speaking) |
| Minimum company capital | €3,000 (SL) | €1 (Ltd) |
| Annual filing complexity | Medium (many quarterly forms) | Medium (bi-monthly VAT, annual CT) |
| Key advantage for SaaS | Large domestic market, lower VAT than IE | Lowest CT rate in EU, strong tech ecosystem |
| Key consideration | IRPF if founder is autónomo | 12.5% is for "trading" income only; verify classification |

### Recommendation for B2B SaaS
- If product primarily serves Spanish market or founder wants to remain in Spain: SL is straightforward
- If product is IP-heavy or planning global scale: Ireland KDB + R&D credit can reduce effective rate to ~6.25% on IP profits
- Common structure: Irish Ltd + Spain non-dom or territorial tax advice — consult a cross-border tax advisor

> Source: This comparison is based on official rates fetched at the time of this command. Always verify with a licensed tax advisor before making incorporation decisions.
```

### Example 3: Non-Spanish Country Setup

```bash
/tax-country-setup DE
```

**Expected Output**:
```
## Germany (DE) Tax Reference Card
Source: bundesfinanzministerium.de | Fetched: 2026-02-21

### Corporate Tax
- Körperschaftsteuer (KSt): 15% + 5.5% Solidaritätszuschlag (SolZ) = 15.825%
- Gewerbesteuer (trade tax): varies by municipality, avg ~14% (Berlin ~14.35%)
- Effective combined rate: ~30% (varies by city)
- Note: No general startup reduced rate; cities like Munich ~17.15% GewSt vs Berlin ~14.35%

### VAT (Umsatzsteuer)
- Standard rate: 19%
- Reduced rate: 7% (food, books, cultural services)
- Kleinunternehmerregelung: exempt if annual revenue < ~€22,000 (voluntary)

### Filing
- USt-Voranmeldung: monthly (if prior year VAT > €7,500) or quarterly
- Due: 10th of following period (extendable by 1 month with Dauerfristverlängerung)
- KSt + GewSt annual returns: July 31 (with Steuerberater: February 28 following year)
- KSt advance payments: March 10, June 10, September 10, December 10

GmbH minimum capital: €25,000 (€12,500 paid in on formation)
```

## Methodology

The command executes in this order:
1. Determines official authority URL for each requested country
2. Performs WebFetch from the official URL to retrieve current rates
3. Extracts: corporate tax rate, VAT rates, key deadlines, IRPF/income tax rates if applicable
4. Formats the reference card in the standard structure above
5. If `--compare` flag provided: fetches second country and builds comparison table
6. Saves country context for the session (subsequent tax-estimation will use these rates)

**Execution time**: 2–3 minutes (1–2 WebFetch calls + formatting)

## Output Format

Every tax-country-setup output includes:

1. **Source declaration**: Official authority URL + fetch date
2. **Corporate tax card**: Standard rate + any reduced/startup rates with conditions
3. **VAT card**: Standard + reduced rates + OSS threshold
4. **Key deadlines**: Top 6–8 most important filing dates with form names
5. **Next step suggestion**: Which skill to run for deeper analysis

## Limitations

- Rates are fetched at time of command execution; rates change with legislation
- Reference card covers main rates only — special regimes (R&D credits, IP boxes) require country-tax-rules skill for full detail
- Social security rates are approximate and income-based systems (Spain RETA, Germany KV/PV/RV/AV) require precise payroll calculation
- This command does not calculate any tax amounts — use tax-estimation for calculations

## Tips

1. **Run before every analysis session**: Tax rates change, especially VAT reduced rates and startup regimes
2. **Save the output**: Paste the reference card into your notes as a quick reference during gestor meetings
3. **Use --compare for incorporation decisions**: The ES vs IE comparison is the most common for EU SaaS founders considering tax optimization
4. **Check the date**: If the fetch date is more than 3 months old (from a previous session), run again to get fresh data

## Integration with Tax Advisor

This command is designed to be the first step in the standard tax analysis workflow:

```bash
# Step 1: Setup country context
/tax-advisor:tax-country-setup ES

# Step 2: Scan deductions from repo
/tax-advisor:deductions-scan

# Step 3: Full VAT analysis
/tax-advisor:vat-analysis

# Step 4: Full tax estimation
/tax-advisor:tax-estimation

# Step 5: Compliance calendar
/tax-advisor:compliance-calendar
```

## Related Commands

- `/tax-advisor:quick-tax-estimate` — Rapid estimate using the rates loaded by this command
- `/tax-advisor:deductions-scan` — Repo scan that runs after country setup
- `/tax-advisor:vat-analysis` — Full VAT classification using loaded country rates
- `/tax-advisor:tax-estimation` — Full tax liability calculation
