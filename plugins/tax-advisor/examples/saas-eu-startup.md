# Example: NebulaPay SL — Spanish B2B SaaS Startup

A complete walkthrough of the tax-advisor plugin for a real-world SaaS scenario, demonstrating all 5 skills in sequence.

## Scenario

**Company**: NebulaPay SL
**Type**: B2B payment analytics SaaS (helps finance teams reconcile Stripe + bank statements)
**Legal structure**: Sociedad Limitada (SL), registered in Spain (Madrid)
**Fiscal year**: January 1 – December 31, 2025
**Status**: First profitable year
**Revenue**: €95,000 gross
**Team**: 1 full-time employee (María, €28,000 gross), 1 German contractor (€12,000/year)

**Customers**:
- 8 Spanish companies: €57,000 (60% of revenue)
- 3 German companies (VAT numbers confirmed): €23,750 (25%)
- 2 French companies (VAT numbers confirmed): €9,500 (10%)
- 1 UK agency (non-EU): €4,750 (5%)

**Repository signals detected**: AWS S3 + EC2, Sentry, Stripe, SendGrid, GitHub Actions, PostgreSQL

---

## Step 1: Country Setup

```bash
/tax-advisor:tax-country-setup ES
```

**Output** (summarized):
```
Spain (ES) Tax Reference Card — Source: aeat.es — Fetched: 2026-02-21

Corporate Tax (IS):
  Standard: 25% | New company: 15% (first two profitable years)

IVA:
  Standard: 21% | Reduced: 10% | Super-reduced: 4%

IRPF (autónomos): 19-47% brackets

Key deadlines:
  Jan 30: Modelo 303 Q4 | Mar 31: Modelo 347
  Apr 20: Modelo 303 Q1 + Modelo 111 | Jul 20: Modelo 303 Q2 + Modelo 111
  Jul 25: Modelo 200 IS | Oct 20: Modelo 303 Q3 + Modelo 111 + Modelo 202
```

**Teaching moment**: NebulaPay is in its first profitable year — the **15% IS rate** instead of 25% applies. This is confirmed with AEAT guidance. Many founders miss this and overpay.

---

## Step 2: Deductions Scan

```bash
/tax-advisor:deductions-scan
```

**Signals detected from NebulaPay's repo**:

| Signal | File | Likely Service | Confidence |
|--------|------|---------------|------------|
| AWS_ACCESS_KEY_ID | .env.example | AWS (S3 + EC2) | HIGH |
| STRIPE_SECRET_KEY | .env.example | Stripe SDK | HIGH |
| SENTRY_DSN | .env.example | Sentry | HIGH |
| SENDGRID_API_KEY | .env.example | SendGrid | HIGH |
| .github/workflows/ci.yml | repo root | GitHub Actions | MEDIUM |
| pg in package.json | package.json | PostgreSQL (RDS) | MEDIUM |
| @sentry/node in package.json | package.json | Sentry (confirms) | HIGH |

**Estimated monthly SaaS subscriptions**: €340–620/month
**Note**: AWS cost unknown — check Cost Explorer for actual figures.

---

## Step 3: Deduction Analysis

```bash
# Full deduction analysis with gap interview
/tax-advisor:deduction-analysis
```

**Gap interview Q&A** (María answers):
1. Monthly gestor fee: €200/month (€2,400/year) ✓
2. Co-working space (Madrid): €300/month (€3,600/year) ✓
3. Training/conferences: €800 (one data engineering conference) ✓
4. Hardware: 1 laptop €1,600 (depreciation 25%/year = €400 deductible year 1) ✓
5. Other: business phone €50/month = €600/year ✓

**Complete Deduction Table**:

| Category | Item | Annual | Deductibility | Evidence |
|----------|------|--------|--------------|---------|
| Cloud Infrastructure | AWS (S3 + EC2) | €4,200 | 100% | Download from AWS Billing |
| Payment Processing Tool | Stripe subscription | €588 | 100% | Stripe Dashboard |
| Monitoring | Sentry (Team plan) | €312 | 100% | Sentry billing |
| Email | SendGrid | €240 | 100% | SendGrid billing |
| CI/CD | GitHub Actions | €228 | 100% | GitHub billing |
| Authentication | (not used) | — | — | — |
| Salary (María) | Gross salary | €28,000 | 100% | Nóminas |
| Employer SS (María) | ~€8,400 (30%) | €8,400 | 100% | SS receipts |
| Contractor (German dev) | Invoice required | €12,000 | 100% | Factura from dev |
| Accounting/gestor | Monthly invoice | €2,400 | 100% | Facturas |
| Co-working (Madrid) | Monthly lease | €3,600 | 100% | Receipts |
| Training/conference | Event invoice | €800 | 100% | Event invoice |
| Hardware depreciation | Laptop year 1 | €400 | 25%/yr | Purchase invoice |
| Business phone | Monthly bill | €600 | 100% | Bills |
| **TOTAL** | | **€61,768** | | |

**Modelo 347 flag**: German contractor paid €12,000 → must be included in Modelo 347 (if they have a Spanish NIF or the payment is via a Spanish account). Confirm with gestor.

**Estimated IS impact** (standard 25% rate): €61,768 × 25% = €15,442 reduction in IS
**Estimated IS impact** (new company 15% rate): €61,768 × 15% = €9,265 reduction in IS

---

## Step 4: VAT Analysis

```bash
/tax-advisor:vat-analysis
```

**Revenue Classification**:

| Customer | Country | Amount | Type | VAT Treatment | VAT Charged |
|----------|---------|--------|------|--------------|------------|
| Spanish clients (8) | ES | €57,000 | B2B domestic | IVA 21% | €11,970 |
| German clients (3) | DE | €23,750 | B2B + VAT nr | Reverse-charge | €0 |
| French clients (2) | FR | €9,500 | B2B + VAT nr | Reverse-charge | €0 |
| UK agency (1) | UK (non-EU) | €4,750 | B2B non-EU | Zero-rated | €0 |
| **TOTAL** | | **€95,000** | | | **€11,970** |

**Invoice text required for German + French invoices**:
```
DE: "Steuerschuldnerschaft des Leistungsempfängers (§ 13b UStG)"
FR: "Auto-liquidation — Article 283 du CGI"
```

**OSS Assessment**:
```
EU B2C cross-border digital services: €0 (all EU customers are B2B)
OSS threshold: €10,000
→ OSS NOT REQUIRED. NebulaPay has no B2C EU customers.
```

**Input VAT Credits** (from deduction-analysis):
```
AWS (Irish billing, 23% IE VAT): €4,200 × 23% = €966 (if AWS bills Irish VAT)
Gestor invoices (Spanish, 21%): €2,400 × 21% = €504
Co-working invoices (Spanish, 21%): €3,600 × 21% = €756
Hardware (Spanish, 21%): €1,600 × 21% = €336

Subtotal input VAT: ~€2,562
Note: German contractor invoice — no Spanish IVA if contractor is German non-resident
```

**Quarterly IVA Calendar**:

| Quarter | IVA Collected | Input VAT | Net IVA | Due Date | Form |
|---------|-------------|-----------|---------|----------|------|
| Q1 (Jan-Mar) | €2,992.50 | €640 | **€2,352.50** | Apr 20 | Modelo 303 |
| Q2 (Apr-Jun) | €2,992.50 | €640 | **€2,352.50** | Jul 20 | Modelo 303 |
| Q3 (Jul-Sep) | €2,992.50 | €640 | **€2,352.50** | Oct 20 | Modelo 303 |
| Q4 (Oct-Dec) | €2,992.50 | €640 | **€2,352.50** | Jan 30 | Modelo 303 |
| **ANNUAL** | **€11,970** | **€2,562** | **€9,408** | | |

**Cash for IVA**: Set aside ~€784/month to cover quarterly IVA payments.

---

## Step 5: Tax Estimation

```bash
/tax-advisor:tax-estimation
```

**Full IS Calculation**:

```
Gross Revenue:                    €95,000
Less: Confirmed deductions:      (€61,768)
= Taxable Base:                   €33,232

IS Rate: 15% (first profitable year — confirmed via AEAT)
= IS Due: €33,232 × 15% = €4,985

Advance payments (Modelo 202):
  Note: First year — no prior year IS, so no advance payments required
  Full IS due: Modelo 200, July 25, 2026

IS advance payments schedule (applies from SECOND year):
  1st advance (April): 18% of prior year IS = €897
  2nd advance (October): 18% of prior year IS = €897
  3rd advance (December): 18% of prior year IS = €897
```

**Scenario Comparison**:

| Scenario | Taxable Base | IS Rate | IS Due | IVA Net | Total Tax |
|----------|-------------|---------|--------|---------|-----------|
| Conservative (few deductions, 25%) | €47,500 | 25% | €11,875 | €9,408 | €21,283 |
| Realistic (confirmed deductions, 15%) | €33,232 | 15% | €4,985 | €9,408 | €14,393 |
| Optimistic (all deductions incl. estimates) | €27,432 | 15% | €4,115 | €8,100 | €12,215 |

**Realistic total: €14,393** (IS €4,985 + IVA net €9,408)

**Monthly cash reserve needed**: €14,393 ÷ 12 = **€1,199/month**

---

## Step 6: Compliance Calendar

```bash
/tax-advisor:compliance-calendar
```

**2026 Filing Calendar for NebulaPay SL**:

| Month | Form | Description | Amount | Deadline |
|-------|------|-------------|--------|----------|
| January | Modelo 303 | Q4 2025 IVA | €2,352.50 | Jan 30 |
| January | Modelo 111 | Q4 IRPF withholdings (María) | ~€1,400 | Jan 30 |
| January | Modelo 190 | Annual IRPF withholdings summary 2025 | Informational | Jan 31 |
| March | Modelo 347 | Third-party ops 2025 (German dev €12k) | Informational | Mar 31 |
| April | Modelo 303 | Q1 2026 IVA | ~€2,352 | Apr 20 |
| April | Modelo 111 | Q1 IRPF withholdings | ~€1,400 | Apr 20 |
| July | Modelo 303 | Q2 2026 IVA | ~€2,352 | Jul 20 |
| July | Modelo 111 | Q2 IRPF withholdings | ~€1,400 | Jul 20 |
| July | **Modelo 200** | **IS annual return 2025** | **~€4,985** | **Jul 25** |
| October | Modelo 303 | Q3 2026 IVA | ~€2,352 | Oct 20 |
| October | Modelo 111 | Q3 IRPF withholdings | ~€1,400 | Oct 20 |
| October | **Modelo 202** | **IS 1st advance payment 2026** | **~€897** | **Oct 20** |
| December | **Modelo 202** | **IS 2nd advance payment 2026** | **~€897** | **Dec 20** |
| Monthly | SS | Social Security (employer + employee) | ~€1,165/mo | Last day |

**Total Social Security (annual)**: ~€8,400 (employer) + ~€1,780 (employee María's contribution)

---

## Key Teaching Moments

### 1. New Company IS Rate (15% vs 25%)
NebulaPay pays €4,985 IS instead of €8,308 (at 25%). **Saving: €3,323**.
This applies automatically for the first two fiscal years with positive taxable base. No application required — just ensure it's claimed on Modelo 200.

### 2. Reverse-Charge for EU B2B
German and French customers DO NOT receive Spanish IVA on their invoices. NebulaPay must:
- Add the reverse-charge text to invoices (see VAT analysis section above)
- Report the sales in Modelo 349 (Recapitulative statement of intra-EU transactions)
- Verify customers' VAT numbers via the EU VIES system (ec.europa.eu/taxation_customs/vies)

Missing reverse-charge compliance is one of the most common IVA audit triggers for Spanish SaaS companies.

### 3. Modelo 347 for German Contractor
Any transaction with a single counterparty exceeding €3,005/year must be declared in Modelo 347. The German contractor (€12,000) clearly exceeds this. NebulaPay must:
- Ensure the contractor has invoiced formally (factura with NIF/VAT number)
- Report the €12,000 in Modelo 347 by March 31

If the contractor has NOT provided formal invoices with a valid tax ID, the deduction is at risk.

### 4. Home Office Deduction Complexity
The scenario does NOT include a home office deduction even though the founder works from home. In Spain, home office deductions for SL directors are legally complex and frequently challenged by AEAT. The decision was made to use the co-working space (€3,600/year) as a clean, fully deductible alternative. **Recommendation**: Avoid home office deductions for SL directors; use co-working if possible.

### 5. AWS Invoice VAT
AWS bills through Amazon Web Services EMEA SARL (Ireland) or Amazon Ireland Ltd. If NebulaPay is VAT-registered, AWS should charge 0% (B2B reverse-charge) and NebulaPay self-assesses the IVA. If AWS incorrectly charges 23% Irish VAT, that can be claimed as input VAT. Always check the AWS invoice carefully.

---

## Final Summary

| Item | Amount |
|------|--------|
| Gross Revenue | €95,000 |
| Total Deductible Expenses | €61,768 |
| Taxable IS Base | €33,232 |
| Impuesto de Sociedades (IS) at 15% | **€4,985** |
| IVA/VAT Net (annual) | **€9,408** |
| **Total Tax 2025** | **€14,393** |
| Effective tax rate on revenue | **15.15%** |
| Monthly cash reserve needed | **€1,199/month** |

---

> **Disclaimer**: This example is for educational purposes only. NebulaPay is a fictional company. All figures are estimates based on assumptions. Consult a licensed gestor/asesor fiscal for your actual tax obligations before filing.
