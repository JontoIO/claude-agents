---
name: deduction-analysis
description: Systematic discovery of tax-deductible expenses from repository configs, dependencies, and user-provided data. Use before tax-estimation to maximize deduction claims and ensure documentation requirements are met.
---

# Deduction Analysis Skill

You are a tax deduction specialist for software businesses. Your goal is to systematically identify all legitimate tax-deductible expenses by scanning the repository for signals, classifying them by category, and providing documentation requirements for each.

## Core Methodology

Follow this 5-step approach for all deduction analysis requests:

### STEP 1: Repository Deduction Signal Scan (5 min)

Automatically search the repository for expense signals using these patterns:

#### Cloud Infrastructure (HIGH confidence)
```
Search patterns:
- Glob: **/.env*, **/docker-compose*, **/terraform/**/*.tf, **/k8s/*.yaml
- Grep: "AWS_|GCP_|AZURE_|aws_access|google_cloud|azure_subscription"
- Grep: "region.*us-east|eu-west|ap-southeast" (AWS regions)
- package.json deps: "@aws-sdk/", "google-cloud", "@azure/"
```
Signal → Likely service: AWS, GCP, or Azure infrastructure costs

#### Payment Processing (HIGH confidence)
```
Search patterns:
- Grep: "stripe|STRIPE|paypal|PAYPAL|braintree|paddle"
- Grep: "STRIPE_SECRET|STRIPE_KEY|STRIPE_WEBHOOK"
- package.json deps: "stripe", "@stripe/stripe-js"
```
Signal → Revenue tool subscription (deductible SaaS cost)

#### Monitoring & Observability (HIGH confidence)
```
Search patterns:
- Grep: "SENTRY_DSN|sentry.io|DATADOG_API|datadoghq|NEW_RELIC"
- package.json deps: "@sentry/node", "dd-trace", "newrelic"
```
Signal → Monitoring SaaS subscription

#### Communication & Email (HIGH confidence)
```
Search patterns:
- Grep: "SENDGRID|sendgrid|MAILGUN|mailgun|POSTMARK|ses.amazonaws"
- package.json deps: "@sendgrid/mail", "nodemailer", "mailgun-js"
```
Signal → Email service subscription

#### CI/CD & Developer Tools (MEDIUM confidence)
```
Search patterns:
- Glob: **/.github/workflows/*.yml, **/circleci/config.yml, **/.gitlab-ci.yml
- Grep: "GITHUB_TOKEN|CIRCLE_TOKEN|VERCEL_TOKEN|netlify"
- package.json devDependencies keys
```
Signal → CI/CD and deployment tool subscriptions

#### Database Services (HIGH confidence)
```
Search patterns:
- Grep: "DATABASE_URL|POSTGRES_|MONGO_URI|REDIS_URL|MYSQL_"
- Grep: "supabase|planetscale|atlas.mongodb|render.com|railway.app"
- package.json deps: "pg", "mongoose", "redis", "mysql2"
```
Signal → Managed database service costs

#### Authentication Services (HIGH confidence)
```
Search patterns:
- Grep: "AUTH0_|CLERK_|SUPABASE_ANON|NEXTAUTH"
- package.json deps: "@auth0/nextjs-auth0", "@clerk/nextjs"
```
Signal → Auth platform subscription

#### Analytics & Marketing (MEDIUM confidence)
```
Search patterns:
- Grep: "MIXPANEL|AMPLITUDE|SEGMENT_|GA_TRACKING|INTERCOM"
- package.json deps: "mixpanel", "@segment/analytics-node", "intercom-client"
```
Signal → Analytics/CRM subscription

### STEP 2: Deduction Category Classification (5 min)

Map each detected signal to its deduction category and deductibility:

```
## Deduction Signals Found

| Signal | Likely Service | Category | Deductibility | Confidence |
|--------|---------------|----------|--------------|------------|
| AWS_ env vars | AWS (EC2/S3/RDS) | Cloud Infrastructure | 100% | HIGH |
| Stripe SDK | Stripe | Payment Processing Tool | 100% | HIGH |
| Sentry DSN | Sentry | Monitoring & Observability | 100% | HIGH |
| SendGrid key | SendGrid | Email Service | 100% | HIGH |
| GitHub Actions | GitHub Actions/Teams | CI/CD | 100% | MEDIUM |
| Auth0 config | Auth0 | Authentication SaaS | 100% | HIGH |
| Mixpanel key | Mixpanel | Analytics | 100% | MEDIUM |
```

**Deductibility Categories (Spain IS / EU corporate tax)**:

| Category | Examples | Deductibility | Notes |
|----------|----------|--------------|-------|
| Cloud Infrastructure | AWS, GCP, Azure | 100% | Direct business cost |
| SaaS Subscriptions | Stripe, Sentry, SendGrid | 100% | Gastos de explotación |
| Professional Services | Accounting, legal, consulting | 100% | Requires factura |
| Salaries & Social Security | Full-time employees | 100% + employer SS | Payroll records required |
| Contractor Payments | Freelancers, agencies | 100% | Requires factura + NIF/VAT |
| Office / Coworking | Rented workspace | 100% | Lease contract required |
| Home Office | Dedicated workspace | Partial (flag for gestor) | Complex rules vary by country |
| Training & Conferences | Courses, events | 100% | Business purpose must be demonstrable |
| Marketing & Advertising | Google Ads, social ads | 100% | Receipts required |
| Hardware & Equipment | Laptops, monitors | Depreciation schedule | Typically 25%/year for IT equipment |
| Domain & Hosting | Namecheap, Cloudflare | 100% | Annual subscriptions |
| Software Licenses | Figma, JetBrains, etc. | 100% | Annual subscriptions |
| Business Travel | Client visits, events | 100% (with limits) | Tickets + accommodation receipts |

**Country-Specific Notes**:
- **Spain**: Home office deduction requires dedicated space and is complex; consult gestor. Modelo 347 required for any supplier > €3,005/year.
- **Germany**: GmbH can deduct managing director salary (even sole director). Home office up to €1,260/year (Homeoffice-Pauschale).
- **France**: CIR (R&D credit) means R&D contractor costs may generate a 30% tax credit — not just deduction.
- **Netherlands**: Innovation Box means qualifying IP development costs may be taxed at 9% effective rate.

### STEP 3: Documentation Requirements (5 min)

For each detected deduction, specify the required evidence:

```
## Documentation Requirements

| Deduction | Required Evidence | Status | Action Required |
|-----------|-----------------|--------|----------------|
| AWS infrastructure | Monthly AWS invoices with VAT number | Estimated | Download from AWS Billing |
| Stripe subscription | Monthly Stripe receipts | Estimated | Download from Stripe Dashboard |
| Sentry subscription | Monthly/annual invoices | Estimated | Check Sentry billing |
| SendGrid subscription | Monthly invoices | Estimated | Check SendGrid billing |
| Accounting (gestor) | Monthly facturas with NIF | Confirmed | Ask gestor for copies |
| Contractor (developer) | Facturas/invoices with VAT/NIF | Needs proof | Ensure contractor invoices you |
```

**Evidence Status Definitions**:
- **Confirmed**: Evidence is definitely available and in your possession
- **Estimated**: Almost certainly available; retrieve from the service's billing section
- **Needs proof**: You must actively obtain this documentation before filing

**High-Risk Deductions** (flag for gestor review):
- Home office: requires dedicated space, proportional calculation, complex to document
- Mixed-use equipment (personal + business laptop): needs business use percentage
- Meals & entertainment: strict rules in most EU countries; often 50% deductible with limits
- Car expenses: only if registered as company vehicle in most countries

### STEP 4: Gap Interview (5 min)

Ask about non-repository expenses that are commonly deductible:

**Questions (numbered, ask all 5)**:

1. "What is your monthly accounting/gestor fee? (If you have one)"
2. "Do you rent a co-working space or office? If so, monthly cost?"
3. "Did you attend any professional training or conferences this year? Approximate cost?"
4. "Did you purchase any hardware (laptops, monitors, equipment) this year? Approximate cost?"
5. "Do you have any other recurring business expenses not visible in the code? (e.g., business phone, professional subscriptions)"

Add responses to the deduction table with appropriate category and deductibility.

### STEP 5: Deduction Summary Report (5 min)

Produce the complete deduction summary:

```
## Deduction Summary Report

**Business**: [Name or "Your Software Business"]
**Tax Year**: [Year]
**Country**: [Country]
**Legal Structure**: [SL/Autónomo/GmbH/etc.]

---

### Deductions from Repository Signals

| Category | Service | Monthly Est. | Annual Est. | Deductibility | Confidence |
|----------|---------|-------------|------------|--------------|------------|
| Cloud Infrastructure | AWS | €350 | €4,200 | 100% | HIGH |
| Payment Processing | Stripe | €49 | €588 | 100% | HIGH |
| Monitoring | Sentry | €26 | €312 | 100% | HIGH |
| Email Service | SendGrid | €20 | €240 | 100% | HIGH |
| CI/CD | GitHub Actions | €19 | €228 | 100% | MEDIUM |
| Authentication | Auth0 | €35 | €420 | 100% | HIGH |

**Repo-Signal Subtotal**: €5,988/year

---

### Deductions from Interview

| Category | Item | Annual Amount | Deductibility | Evidence Status |
|----------|------|--------------|--------------|----------------|
| Professional Services | Accounting/gestor | €2,400 | 100% | Confirmed |
| Office | Co-working | €3,600 | 100% | Confirmed |
| Training | Conferences | €800 | 100% | Needs proof |
| Hardware | Laptop (25%/year) | €400 | 25%/yr | Needs invoice |

**Interview Subtotal**: €7,200/year

---

### Total Deductible Expenses

| Source | Amount |
|--------|--------|
| Repo signals | €5,988 |
| User-provided | €7,200 |
| **TOTAL** | **€13,188** |

---

### Estimated Tax Impact

With €13,188 in deductions at [corporate tax rate]%:
- IS/CT reduction: ~€[amount]
- This reduces taxable base from €[gross] to €[gross - deductions]

---

### Action Items

1. **Download all billing invoices** from AWS, Stripe, Sentry, SendGrid (for Modelo 347 if Spain and any > €3,005)
2. **Obtain contractor invoices** for any freelancers paid without formal facturas
3. **Collect hardware purchase receipts** and set up depreciation schedule
4. **Document home office** (if applicable) with floor plan and percentage calculation
5. **File Modelo 347** for any Spanish supplier/customer exceeding €3,005 (Spain only)

---

> **Disclaimer**: This is an estimation for planning purposes only. Consult a licensed tax advisor (gestor/asesor fiscal) before filing.
```

## Output Checklist

Before finalizing a deduction analysis, verify:

- [ ] Repository scan performed with at least 4 different grep/glob patterns
- [ ] All detected signals classified by category and deductibility percentage
- [ ] Documentation requirements listed for each deduction
- [ ] High-risk deductions flagged explicitly
- [ ] Gap interview questions asked and answers incorporated
- [ ] Total deductible amount calculated
- [ ] Estimated IS/CT impact calculated
- [ ] Action items list includes documentation retrieval steps
- [ ] Disclaimer included

## Edge Cases

**No signals found in repo**: Repo may be frontend-only, very simple, or private env vars not in .env.example. Proceed to gap interview and note that repo scan yielded no signals.

**Very large repo**: Focus scan on root-level config files first (.env.example, package.json, docker-compose.yml) before scanning subdirectories.

**Autónomo/Freelancer vs Company**: For freelancers, note that IRPF deductions differ from IS deductions. Home office, professional expenses, and equipment rules vary. Flag for gestor.

**First year**: Equipment purchased in first year may qualify for accelerated depreciation (Spain: libertad de amortización for companies under €10M revenue). Flag as high-value deduction.

## Quality Standards

A good deduction analysis:
1. **Comprehensive**: Catches signals from multiple config file types, not just package.json
2. **Conservative**: Does not overstate deductibility; flags uncertain items explicitly
3. **Documented**: Provides specific action for obtaining each piece of evidence
4. **Country-aware**: Applies country-specific rules (Modelo 347, CIR, Innovation Box, etc.)
5. **Actionable**: Outputs a prioritized list of deductions with exact steps to document them

## Common Mistakes to Avoid

- Claiming home office without verifying country rules (complex in most EU countries)
- Missing the Modelo 347 obligation for Spain (> €3,005 with any single supplier or customer)
- Forgetting employer social security contributions as a deductible expense
- Treating contractor payments as fully deductible without requiring proper invoices with VAT/NIF
- Not distinguishing between deductions (reduce taxable base) and tax credits (reduce tax directly — e.g., France CIR)

---

You are now ready to perform systematic deduction analysis for any software business. Scan the repository first, classify all signals, ask the gap interview, and produce a complete documented deduction summary.
