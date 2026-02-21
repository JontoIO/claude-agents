# Quick Tax Estimate Command

Provides a rapid EU tax estimate from a revenue figure and country/structure flags. No repo scan required. Results in under 2 minutes.

## Purpose

Get a ballpark tax figure when:
- Evaluating tax implications of a revenue milestone
- Comparing tax burden across EU countries for relocation decisions
- Answering "how much should I set aside for taxes this year?" quickly
- Preparing for an investor conversation that touches on tax efficiency

## When to Use

**Use quick-tax-estimate when**:
- Need a rough figure in minutes, not hours
- Accuracy of ±30–35% is acceptable for the decision at hand
- Comparing relative tax burden across countries or structures
- Early-stage planning (pre-revenue or early revenue)

**Use full tax-estimation skill when**:
- Need formula-transparent calculation with three scenarios
- Planning actual quarterly payments
- Sharing with a gestor or accountant
- Revenue > €100,000 or cross-border VAT complexity exists
- Making decisions about incorporation country or legal structure change

## Command Format

```bash
/quick-tax-estimate [annual-revenue] --country [code] --structure [type]
```

### Parameters

```
[annual-revenue]        Required. Annual gross revenue in EUR (e.g., 85000)
--country [code]        Required. One of: ES, DE, FR, IT, NL, PT, PL, IE
--structure [type]      Required. One of: sl, ltd, gmbh, bv, sarl, srl, autónomo, freelancer
```

### Optional Parameters

```
--expenses [amount]     Known annual expenses (reduces taxable base)
--employees [number]    Number of employees (affects SS estimate)
--b2b-eu-pct [0-100]   % of revenue from EU B2B customers (reverse-charge, reduces IVA)
--new-company           Flag: first profitable year (applies startup rates where available)
```

## Examples

### Example 1: Spanish SL — B2B SaaS

```bash
/quick-tax-estimate 85000 --country ES --structure sl
```

**Expected Output**:
```
## Quick Tax Estimate — Spanish SL, €85,000 Revenue
Rates: aeat.es (Spain) | Accuracy: ±35%

### Assumptions Used
- Expenses estimated: 40% of revenue (~€34,000) — typical SaaS profile
- Revenue: 100% domestic B2B (conservative — all IVA collected)
- Standard IS rate: 25% (use --new-company flag for 15% if eligible)

### Corporate Tax (IS)
Taxable Base = €85,000 − €34,000 = €51,000
IS at 25% = **€12,750**
(With --new-company flag at 15%: IS = €7,650, saving €5,100)

### IVA Net (estimated)
Collected IVA: €85,000 × 21% = €17,850
Input VAT credits (estimated, ~20% of expenses): €1,428
Net IVA payable: **~€16,422**
Note: If customers are EU B2B with VAT numbers, IVA collected drops significantly

### Total Estimated Tax Liability
| Tax | Conservative | Realistic |
|-----|-------------|-----------|
| IS | €12,750 (25%) | €8,500 (25%, more deductions) |
| IVA net | €16,422 | €9,500 (if 50% EU B2B reverse-charge) |
| **TOTAL** | **~€29,172** | **~€18,000** |

### Cash Reserve Recommendation
Set aside €[1,500–2,430]/month depending on actual B2B/B2C mix

Accuracy: ±35% | Run `/tax-advisor:tax-estimation` for precise calculation
```

### Example 2: Spanish Autónomo — Freelance Developer

```bash
/quick-tax-estimate 45000 --country ES --structure autónomo
```

**Expected Output**:
```
## Quick Tax Estimate — Autónomo (Spain), €45,000 Revenue
Rates: aeat.es | Accuracy: ±35%

### Assumptions
- Deductible expenses: ~€8,000 (home office partial, tools, accounting)
- RETA (social security): ~€400/month average = €4,800/year (deductible)
- Net professional income: €45,000 − €8,000 − €4,800 = €32,200

### IRPF Calculation (simplified)
0 − €12,450: 19% = €2,365.50
€12,451 − €20,200: 24% = €1,860
€20,201 − €32,200: 30% = €3,600
**IRPF total: ~€7,825**
Quarterly Modelo 130: ~€1,956/quarter (20% of net quarterly income)

### IVA Net
Collected: €45,000 × 21% = €9,450
Input VAT (estimated): €600
**Net IVA: ~€8,850**

### Social Security (RETA)
~€400/month = **€4,800/year**
(Income-based since 2023 — verify current bracket at SS.gob.es)

### Total Annual Obligations
| Item | Amount |
|------|--------|
| IRPF | ~€7,825 |
| IVA net | ~€8,850 |
| RETA | ~€4,800 |
| **TOTAL** | **~€21,475** |

Effective rate: ~47.7% of gross revenue
Monthly set-aside: ~€1,790/month

Accuracy: ±35% | Note: At this income level, SL structure may reduce tax — run full analysis to compare.
```

### Example 3: Irish Ltd — B2B SaaS

```bash
/quick-tax-estimate 120000 --country IE --structure ltd
```

**Expected Output**:
```
## Quick Tax Estimate — Irish Ltd, €120,000 Revenue
Rates: revenue.ie (Ireland) | Accuracy: ±35%

### Assumptions
- Expenses estimated: 45% of revenue (~€54,000)
- Revenue classification: B2B trading income (12.5% CT rate applies)
- VAT: registered, standard 23%

### Corporation Tax (CT)
Taxable Base = €120,000 − €54,000 = €66,000
CT at 12.5% (trading income) = **€8,250**

### VAT Net
Collected: €120,000 × 23% = €27,600
Input VAT (estimated): €3,000
**Net VAT: ~€24,600**
Note: If customers are EU B2B with VAT numbers → reverse-charge applies, net VAT drops significantly

### Total Estimated
| Tax | Amount |
|-----|--------|
| Corporation Tax | €8,250 |
| VAT net | €24,600 (if domestic only) |
| **TOTAL** | **~€32,850** |

CT comparison vs Spain: Spanish SL at same revenue = ~€18,750 IS (25%)
Ireland saves ~€10,500 in corporate tax — but VAT at 23% vs 21% partially offsets

Accuracy: ±35% | Use --b2b-eu-pct flag to model reverse-charge impact on VAT
```

## Methodology

The command uses simplified formulas for speed:

### Corporate Tax Formula
```
Taxable Base = Annual Revenue × (1 − Expense Ratio)
  where Expense Ratio defaults to:
    - SaaS/software companies: 40-45%
    - Freelancers/autónomos: 25-30%
    - Adjusted to 60-70% if --employees flag provided (higher salary costs)

Corporate Tax = Taxable Base × Country CT Rate
  (startup rate applied if --new-company flag provided and country has one)
```

### VAT/IVA Formula
```
VAT Collected = Revenue × Standard VAT Rate × (1 − B2B EU Reverse-Charge Pct)
Input VAT Credits = Expenses × 0.20 × Standard VAT Rate (rough estimate)
Net VAT = VAT Collected − Input VAT Credits
```

### IRPF (Spain autónomo only)
```
Net Professional Income = Revenue − Expenses − RETA Social Security
IRPF = Apply progressive brackets to Net Professional Income
```

### Default Expense Ratios by Structure
| Structure | Default Expense Ratio | Rationale |
|-----------|---------------------|-----------|
| SL/Ltd (no employees) | 35% | Cloud, tools, accounting, contractor |
| SL/Ltd (1-2 employees) | 50% | Above + salary + employer SS |
| SL/Ltd (3-5 employees) | 65% | Significant payroll |
| Autónomo/Freelancer | 25% | Mostly RETA + small tools |

## Output Format

Every quick-tax-estimate output includes:

1. **Header**: Country, structure, revenue, accuracy warning
2. **Assumptions**: Explicit default assumptions used (override with flags)
3. **Corporate/Income Tax**: Formula-visible calculation
4. **VAT/IVA**: Net position estimate
5. **Total table**: All taxes in a clean summary table
6. **Cash reserve**: Monthly set-aside recommendation
7. **Accuracy note + next step**: Always points to full tax-estimation for precision

## Limitations

- **±30–35% accuracy** — suitable for planning, not for filing or investor materials
- Does not perform WebFetch for live rates; uses reference rates from country-tax-rules skill
- Does not scan the repository (use `/deductions-scan` first for better deduction estimates)
- Does not model cross-border complexity (OSS, multiple registrations) — use vat-analysis
- Does not account for prior year losses, R&D credits, or special IP regimes
- Social security estimates are ranges; actual SS depends on income level and country rules

## Tips

1. **Use --new-company** if this is your first profitable year in Spain — the 15% IS rate instead of 25% changes the estimate significantly
2. **Use --b2b-eu-pct** if most of your customers are EU businesses with VAT numbers — reverse-charge dramatically reduces your IVA liability
3. **Compare before deciding**: Run the command for multiple countries to compare tax burden before an incorporation decision
4. **Use as floor/ceiling**: The conservative scenario is a reasonable worst-case; the realistic scenario with good expense documentation is likely achievable

## Integration with Other Skills

```bash
# Quick estimate workflow:
/tax-advisor:tax-country-setup ES              # Load country context (optional but recommended)
/tax-advisor:quick-tax-estimate 80000 --country ES --structure sl --new-company
                                               # Get quick ballpark in 2 minutes

# Upgrade to full analysis:
/tax-advisor:deductions-scan                   # Auto-detect deductions from repo
/tax-advisor:tax-estimation                    # Full 6-step analysis with live rates
```

## Related Commands

- `/tax-advisor:tax-country-setup` — Loads live rates used by this command
- `/tax-advisor:deductions-scan` — Improves estimate accuracy by detecting actual expenses
- `/tax-advisor:vat-analysis` — Detailed VAT analysis for cross-border complexity
- `/tax-advisor:compliance-calendar` — Turns this estimate into a monthly deadline calendar
