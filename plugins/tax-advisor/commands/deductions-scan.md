# Deductions Scan Command

Runs an automated grep/glob scan of the repository for tax-deductible expense signals without requiring user input. Produces a preliminary deduction table in 3–5 minutes.

## Purpose

Get a rapid inventory of likely deductible business expenses detectable in the codebase before a full deduction-analysis or tax-estimation. Useful for:
- Getting a quick sense of deductible infrastructure and SaaS costs
- Preparing for a financial interview by knowing what's already confirmed
- Auditing a new project to understand its cost structure

## When to Use

**Use deductions-scan when**:
- You want a fast automated snapshot of repo-detectable deductions
- Starting a tax analysis session and want to prime the deduction list
- Sharing deduction signals with a gestor without running the full analysis
- Analyzing a repo you didn't build to understand its cost profile

**Use full deduction-analysis skill when**:
- You need documentation requirements for each deduction
- You want the gap interview to add non-repo expenses (co-working, accounting, hardware)
- You need estimated amounts and total deductible sum
- Preparing for the IS/CT calculation in tax-estimation

## Command Format

```bash
/deductions-scan [--path /path/to/repo]
```

### Parameters

```
--path [path]    Optional. Path to scan. Defaults to current directory.
                 Use when the main project files are in a subdirectory.
```

## Examples

### Example 1: Scan Current Directory

```bash
/deductions-scan
```

**Expected Output**:
```
## Deductions Scan — Current Directory
Scanned: /path/to/project
Duration: ~3 minutes
Country context: Spain (ES) [set by previous tax-country-setup, or default]

### Signals Detected

| Signal Found | Likely Service | Estimated Monthly Cost | Deductibility | Confidence |
|-------------|---------------|----------------------|--------------|------------|
| AWS_ACCESS_KEY_ID in .env.example | AWS (EC2/S3/RDS) | €200–500 | 100% | HIGH |
| STRIPE_SECRET_KEY in .env.example | Stripe | €49–99 (fees are % of revenue, not subscription) | 100% | HIGH |
| @sentry/node in package.json | Sentry error monitoring | €26–80 | 100% | HIGH |
| SENDGRID_API_KEY in .env.example | SendGrid email | €20–99 | 100% | HIGH |
| .github/workflows/*.yml found | GitHub Actions | €0–21 (free tier likely) | 100% | MEDIUM |
| AUTH0_DOMAIN in .env.example | Auth0 | €35–100 | 100% | HIGH |
| docker-compose.yml found (postgres service) | Managed DB or local | €25–50 | 100% | MEDIUM |

### Not Found
- GCP/Azure (likely AWS-only stack)
- Datadog/New Relic (using Sentry for monitoring)
- Intercom/Zendesk (no customer support tool detected)
- CI/CD beyond GitHub Actions

### Preliminary Totals (estimated)
- Monthly SaaS subscriptions detected: €355–849
- Annual SaaS total: €4,260–10,188
- Note: AWS costs depend heavily on usage — review AWS Cost Explorer for actual amounts

### Next Steps
1. Run `/tax-advisor:deduction-analysis` for documentation requirements and gap interview
2. Run `/tax-advisor:tax-estimation` for full IS/IVA calculation using these deductions
3. Download billing invoices from: AWS Billing, Stripe Dashboard, Sentry, SendGrid

> Confidence levels: HIGH = explicit config/key found | MEDIUM = import pattern found | LOW = dependency name only
```

### Example 2: Scan Specific Subdirectory

```bash
/deductions-scan --path ./backend
```

**Expected Output**:
```
## Deductions Scan — ./backend
Scanned: /path/to/project/backend
Note: Scanning backend only — some configs may be in root or other directories

### Signals Detected

| Signal Found | Likely Service | Est. Monthly Cost | Deductibility | Confidence |
|-------------|---------------|------------------|--------------|------------|
| AWS_S3_BUCKET in config/storage.ts | AWS S3 | €5–50 | 100% | HIGH |
| import Stripe from 'stripe' in payments/index.ts | Stripe SDK | Stripe subscription | 100% | HIGH |
| require('@sentry/node') in app.ts | Sentry | €26–80 | 100% | HIGH |
| pg in package.json | PostgreSQL (possibly managed RDS) | €25–100 | 100% | MEDIUM |

### Files Scanned
- package.json ✓
- .env.example ✓ (not found — using config/*.ts patterns)
- docker-compose.yml ✗ (not found in ./backend)
- Dockerfile ✓

### Recommendation
Run `/deductions-scan` (no --path) to also scan root directory for .env.example
and docker-compose.yml which often contain additional service configs.
```

## Scan Methodology

The command runs these searches in sequence (< 3 minutes total):

### Phase 1: Environment & Config Files (30 sec)
```
Glob: **/.env.example, **/.env.sample, **/.env.template
Grep in found files: AWS_|STRIPE_|SENTRY_|SENDGRID_|AUTH0_|DATADOG_|GCP_|AZURE_
```

### Phase 2: Package Dependencies (30 sec)
```
Read: package.json (Node.js), requirements.txt (Python), go.mod (Go), Gemfile (Ruby)
Match against known SaaS SDK list:
  @aws-sdk/* → AWS
  stripe, @stripe/* → Stripe
  @sentry/* → Sentry
  @sendgrid/* → SendGrid
  @auth0/* → Auth0
  dd-trace → Datadog
  newrelic → New Relic
  @google-cloud/* → GCP
  @azure/* → Azure
```

### Phase 3: Infrastructure Files (30 sec)
```
Glob: **/docker-compose*.yml, **/Dockerfile, **/terraform/**/*.tf, **/k8s/*.yaml
Grep in Dockerfiles: FROM postgres, FROM redis, FROM mongo (database signals)
Grep in terraform: aws_instance, google_compute, azurerm_ (cloud provider signals)
```

### Phase 4: CI/CD Files (30 sec)
```
Glob: **/.github/workflows/*.yml, **/circleci/config.yml, **/.gitlab-ci.yml, **/bitbucket-pipelines.yml
Presence → CI/CD tool subscription signal
```

### Phase 5: Source Code Quick Scan (60 sec)
```
Grep in **/*.ts, **/*.js, **/*.py (top-level files only, not node_modules):
  Pattern: import.*stripe|require.*sentry|import.*aws-sdk|import.*sendgrid
  Pattern: process.env.STRIPE|process.env.AWS|os.environ.get('AWS
```

## Output Format

Every deductions-scan output includes:

| Column | Description |
|--------|-------------|
| Signal Found | Exact file path + key/import detected |
| Likely Service | Human-readable service name |
| Estimated Monthly Cost | Range based on typical pricing for that service |
| Deductibility | % deductible under EU corporate tax |
| Confidence | HIGH / MEDIUM / LOW |

**Confidence Definitions**:
- **HIGH**: Explicit API key or secret found in env config (confirms service is actively used)
- **MEDIUM**: Import or dependency found (service is integrated but usage level unknown)
- **LOW**: Dependency name found only (may be installed but not actively used)

## Limitations

- Cannot determine actual spend — only signals that a service is used
- Does not scan for non-SaaS expenses (salaries, office, accounting) — these require the gap interview in deduction-analysis
- Private environment variables (not in .env.example) will not be detected
- Monorepos with complex directory structures may need `--path` to target the right subdir
- Some services are rebranded (e.g., Vercel Postgres, PlanetScale) and may not match known patterns

## Tips

1. **Run from the project root** for the most complete scan — .env.example and package.json are usually at root
2. **Check if .env.example exists** — if the project uses only environment variables in CI/CD (no .env.example), the scan will rely on source code imports only
3. **Stripe signals ≠ Stripe subscription cost** — Stripe fees are % of revenue processed, not a fixed SaaS subscription. The deductible cost is the Stripe fees paid, found in your Stripe Dashboard
4. **AWS signals require manual cost lookup** — AWS cost depends entirely on usage. Always check AWS Cost Explorer for actual monthly spend
5. **Use HIGH confidence signals as your primary deduction list** — MEDIUM/LOW signals are useful leads but need verification

## Integration with Other Skills

```bash
# Complete deduction workflow:
/tax-advisor:deductions-scan          # Phase 1: automated repo scan (this command)
/tax-advisor:deduction-analysis       # Phase 2: full analysis + documentation + gap interview
/tax-advisor:tax-estimation           # Phase 3: use deductions in IS/CT calculation
```

## Related Commands

- `/tax-advisor:tax-country-setup` — Run first to set country context for deductibility rates
- `/tax-advisor:deduction-analysis` — Full skill with documentation requirements and gap interview
- `/tax-advisor:quick-tax-estimate` — Rapid estimate that uses deductions found by this scan
