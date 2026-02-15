# Cost Estimation Skill

A systematic framework for estimating software project costs including API usage, infrastructure, development, and operational expenses.

## Overview

The Cost Estimation skill provides a structured 5-step approach to calculate comprehensive project costs. It works for any software project type and adapts to available data sources.

## Purpose

- Calculate accurate cost estimates for software projects
- Break down costs into manageable categories
- Model different usage scenarios (low/medium/high)
- Identify cost optimization opportunities
- Provide data-driven budget planning

## When to Use

- Beginning a new project and need budget estimates
- Evaluating the financial viability of a feature
- Planning for scaling and growth
- Comparing costs across architectural options
- Quarterly budget reviews and updates
- Investigating cost overruns or unexpected expenses

## Key Cost Categories

### 1. API Costs
- **Claude API**: Token-based pricing for AI features
- **Third-party APIs**: Authentication (Auth0, Okta), payments (Stripe, PayPal), analytics (Mixpanel, Segment), maps (Google Maps, Mapbox), communications (Twilio, SendGrid)
- **Calculation**: Requests per day × cost per request × 30 days

### 2. Infrastructure Costs
- **Compute**: EC2, Cloud Run, App Engine, Lambda
- **Storage**: S3, Cloud Storage, object storage
- **Databases**: RDS, Cloud SQL, DynamoDB, Firestore
- **Networking**: Load balancers, CDN, data transfer
- **Calculation**: Resource units × unit price × usage hours

### 3. Development Costs
- **Engineering**: Senior dev ($80-150/hr), junior dev ($40-80/hr), DevOps ($70-120/hr)
- **Design**: UI/UX designer ($60-100/hr), product designer ($70-110/hr)
- **Management**: Project manager ($60-100/hr), product manager ($70-120/hr)
- **Calculation**: Hours required × hourly rate by role

### 4. Operational Costs
- **Monitoring**: DataDog, New Relic, CloudWatch
- **Support**: Customer service tools, ticket systems
- **Maintenance**: Bug fixes, updates, dependency management
- **Calculation**: Typically 10-20% of development costs

### 5. Additional Costs
- **Compliance**: SOC2 audit ($15k-50k), GDPR consultant ($5k-20k), penetration testing ($10k-30k)
- **Legal**: Terms of service, privacy policy ($2k-10k)
- **Marketing**: Initial launch, customer acquisition
- **Insurance**: Liability, cybersecurity insurance

## Framework: 5-Step Process

### Step 1: Data Collection
Gather project information from multiple sources.

**Automatic (via MCP Tools)**:
- Read `package.json`, `requirements.txt`, `go.mod` for dependencies
- Analyze `Dockerfile`, `docker-compose.yml` for infrastructure
- Scan Terraform, CloudFormation configs for cloud resources
- Check `.env.example` for API integrations
- Review git commit history for development velocity

**Manual (User Questions)**:
- "What is your expected monthly active user count?"
- "How many Claude API calls will a typical user make per session?"
- "What is the average token count per Claude API request?"
- "What is your team composition (roles and count)?"
- "What cloud provider are you using?"
- "Are there specific regulatory requirements?"

### Step 2: Cost Categorization
Organize costs into categories for clarity.

**Template**:
```
API Costs
├── Claude API
├── Authentication (Auth0, Okta)
├── Payments (Stripe, PayPal)
└── Other third-party services

Infrastructure Costs
├── Compute (EC2, containers)
├── Storage (S3, databases)
├── Networking (CDN, load balancers)
└── Monitoring & logging

Development Costs
├── Engineering (senior, junior, DevOps)
├── Design (UI/UX, product)
└── Management (project, product)

Operational Costs
├── Maintenance (ongoing support)
├── Customer support
└── Compliance & legal
```

### Step 3: Usage Modeling
Model usage patterns for accurate projections.

**Key Metrics**:
- Daily Active Users (DAU)
- Monthly Active Users (MAU)
- Requests per user per day
- Data volume per user
- Storage growth rate
- Peak traffic multiplier (2-5x average)

**Scenarios**:
- **Low**: Conservative estimate (20th percentile)
- **Medium**: Expected estimate (50th percentile)
- **High**: Growth estimate (80th percentile)

**Example**:
```
SaaS Application Usage Model
- Low: 100 users, 5 API calls/user/day, 500 tokens/call
- Medium: 1,000 users, 10 API calls/user/day, 1,000 tokens/call
- High: 10,000 users, 20 API calls/user/day, 2,000 tokens/call
```

### Step 4: Cost Calculation
Calculate costs using current pricing data.

**Claude API Calculation** (as of January 2025):
```
Claude 3.5 Sonnet:
- Input: $3.00 per million tokens
- Output: $15.00 per million tokens

Monthly Cost Formula:
(Users × Calls/User/Day × Tokens/Call × Price/1M tokens × 30 days) / 1,000,000

Example (1,000 users, 10 calls/day, 1,000 tokens/call, 50% input/output):
Input: 1,000 × 10 × 1,000 × 0.5 × $3.00 × 30 / 1,000,000 = $450
Output: 1,000 × 10 × 1,000 × 0.5 × $15.00 × 30 / 1,000,000 = $2,250
Total: $2,700/month
```

**AWS Infrastructure Calculation**:
```
EC2 (t3.medium, 2 vCPU, 4GB RAM):
- On-demand: $0.0416/hour × 730 hours = $30.37/month
- Reserved (1-year): ~$20/month (35% savings)

RDS PostgreSQL (db.t3.small):
- Instance: $0.034/hour × 730 hours = $24.82/month
- Storage: 100GB × $0.115/GB = $11.50/month
- Total: $36.32/month

S3 Storage:
- Standard: $0.023/GB × 1TB = $23.55/month
- Requests: 1M PUT/COPY/POST = $5.00
- Data transfer: 500GB out = $45.00

Total AWS: ~$165/month (basic setup)
```

**Development Cost Calculation**:
```
Team Composition:
- 1 Senior Developer: $100/hr × 160 hrs/month = $16,000
- 1 Junior Developer: $60/hr × 160 hrs/month = $9,600
- 1 Designer: $80/hr × 80 hrs/month = $6,400

Total: $32,000/month ($384,000/year)
```

### Step 5: Reporting
Present cost breakdown with actionable recommendations.

**Report Template**:
```markdown
## Cost Estimate Summary

**Project**: [Project Name]
**Date**: [Date]
**Scenario**: [Low/Medium/High]
**Time Period**: Monthly / Annual

### Cost Breakdown

| Category           | Monthly   | Annual     | % of Total |
|--------------------|-----------|------------|------------|
| Claude API         | $2,700    | $32,400    | 8%         |
| Infrastructure     | $500      | $6,000     | 1.5%       |
| Third-party APIs   | $300      | $3,600     | 1%         |
| Development        | $32,000   | $384,000   | 89%        |
| Operations         | $500      | $6,000     | 1.5%       |
| **TOTAL**          | **$36,000** | **$432,000** | **100%**   |

### Key Assumptions
- 1,000 monthly active users
- 10 Claude API calls per user per day
- 1,000 tokens per call (50% input, 50% output)
- 2 developers, 1 part-time designer
- AWS infrastructure (EC2, RDS, S3)
- 10% operations overhead

### Cost Optimization Recommendations

1. **Claude API** ($2,700/mo)
   - Implement prompt caching (potential 20-30% savings)
   - Optimize token usage through prompt engineering
   - Consider batch processing for non-real-time requests
   - Potential savings: $500-800/month

2. **Infrastructure** ($500/mo)
   - Use reserved instances for predictable workloads (35% savings)
   - Implement auto-scaling to reduce idle capacity
   - Use S3 lifecycle policies for old data
   - Potential savings: $100-150/month

3. **Development** ($32,000/mo)
   - Largest cost category - focus on efficiency
   - Use AI coding assistants to boost productivity
   - Prioritize features with highest user value
   - Consider contract developers for specialized tasks

### Scenario Comparison

| Scenario | Users  | Monthly Cost | Annual Cost |
|----------|--------|--------------|-------------|
| Low      | 100    | $34,500      | $414,000    |
| Medium   | 1,000  | $36,000      | $432,000    |
| High     | 10,000 | $52,000      | $624,000    |

### Risk Factors
- API usage may spike 2-5x during viral growth
- Development costs are fixed regardless of user count
- Infrastructure scales with users (watch for threshold jumps)
```

## Common Pricing Sources

### APIs (as of January 2025)
- **Claude API**: https://anthropic.com/pricing
  - Sonnet: $3 input, $15 output per 1M tokens
  - Opus: $15 input, $75 output per 1M tokens
  - Haiku: $0.25 input, $1.25 output per 1M tokens

- **Auth0**: https://auth0.com/pricing
  - Free: 7,500 MAU
  - Essentials: $35/month + $0.05/MAU
  - Professional: $240/month + $0.07/MAU

- **Stripe**: https://stripe.com/pricing
  - 2.9% + $0.30 per transaction
  - $15-$500/month for premium features

### Cloud Infrastructure
- **AWS**: https://aws.amazon.com/pricing/
- **GCP**: https://cloud.google.com/pricing/
- **Azure**: https://azure.microsoft.com/pricing/

### Monitoring & Tools
- **DataDog**: $15-31/host/month
- **New Relic**: $0.25/GB ingested + $0.50/100M queries
- **Sentry**: $26-80/month for error tracking

## Examples

### Example 1: Minimal SaaS MVP
```
Scenario: React app + Node.js API + PostgreSQL
Users: 50 beta users
Claude usage: 5 calls/user/day, 500 tokens/call

Monthly Costs:
- Claude API: $56 (low usage)
- Vercel hosting: $20 (Pro plan)
- Supabase: $25 (Pro tier)
- Auth0: $35 (Essentials)
- Development: $16,000 (1 full-stack dev)
Total: $16,136/month

Key insight: Development is 99% of cost at this stage
```

### Example 2: Growing API Service
```
Scenario: Python API with Claude integration
Users: 5,000 API consumers
Claude usage: 100 calls/user/month, 2,000 tokens/call

Monthly Costs:
- Claude API: $15,000 (1B tokens/month)
- AWS: $800 (EC2, RDS, load balancer)
- DataDog: $150 (monitoring)
- Development: $25,000 (1.5 devs + 0.5 DevOps)
Total: $40,950/month

Key insight: API costs now 37% of total - optimization critical
```

### Example 3: Enterprise Platform
```
Scenario: Multi-tenant SaaS with AI features
Users: 50,000 enterprise users
Claude usage: 50 calls/user/month, 1,500 tokens/call

Monthly Costs:
- Claude API: $84,375 (3.75B tokens/month)
- AWS: $5,000 (multi-region, high availability)
- Third-party APIs: $2,000 (Auth0, Stripe, SendGrid)
- Development: $80,000 (5 devs, 2 DevOps, 1 designer)
- Operations: $15,000 (support, compliance)
Total: $186,375/month ($2.2M/year)

Key insight: API costs now largest category - require enterprise pricing
```

## Tips and Best Practices

1. **Always model multiple scenarios** - Don't rely on single estimate
2. **Include 20-30% buffer** for unexpected costs
3. **Update pricing data quarterly** - Cloud prices change frequently
4. **Track actual vs estimated** - Improve accuracy over time
5. **Development is typically 70-80%** of total cost for new projects
6. **API costs grow with users** while development costs are more fixed
7. **Consider reserved pricing** for predictable infrastructure (30-50% savings)
8. **Monitor usage patterns** to catch anomalies early
9. **Optimize high-volume APIs first** - Biggest impact on cost
10. **Plan for compliance early** - SOC2, GDPR audits are expensive

## Integration with Other Skills

- **monetization-planning**: Use cost estimates to set profitable pricing tiers
- **financial-risk-assessment**: Identify cost overrun risks and mitigation strategies
- **roi-analysis**: Calculate break-even point and payback period from costs

## Limitations

- Estimates have ±20% accuracy under typical conditions
- Pricing changes frequently - verify current rates
- Doesn't account for volume discounts (contact vendors)
- Human cost estimates vary by geography and experience
- Doesn't include one-time costs (setup, migration, training)

## Version History

- **1.0.0** (January 2025): Initial release with 5-step framework

## Related Resources

- [Financial Advisor Agent](../../agents/financial-advisor/README.md)
- [Quick Cost Estimate Command](../../commands/quick-cost-estimate.md)
- [Monetization Planning Skill](../monetization-planning/README.md)
