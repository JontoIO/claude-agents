# Financial Risk Assessment Skill

A systematic framework for identifying, analyzing, and mitigating financial risks in software projects.

## Overview

The Financial Risk Assessment skill provides a structured approach to identify potential financial threats, evaluate their impact, and develop mitigation strategies. It covers regulatory compliance, cost overruns, integration risks, and revenue challenges.

## Purpose

- Identify financial risks before they become problems
- Assess severity and probability of each risk
- Ensure compliance with regulatory requirements
- Develop actionable mitigation strategies
- Create monitoring frameworks for early warning
- Protect project financial health

## When to Use

- Beginning a new project to identify risks early
- Before making major architectural decisions
- When entering regulated markets (finance, healthcare, education)
- During security audits or compliance reviews
- When experiencing unexpected cost increases
- Before fundraising or investor presentations
- Quarterly risk review and assessment updates

## Key Risk Categories

### 1. Regulatory Compliance Risks
Financial penalties for non-compliance with laws and regulations.

**Examples**:
- **GDPR** (EU): €20M or 4% of annual revenue (whichever is higher)
- **CCPA** (California): Up to $7,500 per violation
- **HIPAA** (Healthcare): $100-50,000 per violation, up to $1.5M/year
- **PCI-DSS** (Payment cards): $5,000-100,000/month for non-compliance
- **SOC2** (Enterprise): Not a fine, but loss of enterprise customers
- **COPPA** (Children): Up to $43,280 per violation

### 2. Cost Overrun Risks
Unexpected increases in operational costs.

**Examples**:
- API usage spikes from viral growth or bot attacks
- Infrastructure scaling costs exceeding projections
- Third-party service price increases (20-50% annually is common)
- Technical debt requiring expensive refactoring
- Security breach remediation costs
- Extended development timelines

### 3. Integration Risks
Financial exposure from third-party dependencies.

**Examples**:
- API deprecation requiring costly replacement
- Vendor lock-in preventing cost optimization
- Service downtime causing revenue loss
- Rate limits requiring expensive tier upgrades
- Integration costs exceeding value provided
- License compliance violations

### 4. Revenue Risks
Threats to income and monetization strategy.

**Examples**:
- High customer churn rates (>5% monthly is concerning)
- Payment processing fees eating margins (2-3% typical)
- Pricing misaligned with usage patterns
- Free tier abuse without conversion to paid
- Customer acquisition cost (CAC) exceeding lifetime value (LTV)
- Market competition forcing price reductions

## Framework: 5-Step Process

### Step 1: Risk Identification
Catalog all potential financial risks across categories.

**Method**: Systematic review of project components:
- Review regulatory requirements for target markets
- Analyze API usage patterns and scaling behavior
- Examine third-party dependencies and contracts
- Evaluate revenue model and conversion assumptions
- Check security vulnerabilities with financial impact
- Assess team capacity and delivery risks

### Step 2: Impact Analysis
Assess severity (Low/Medium/High) and probability (Unlikely/Possible/Likely).

**Risk Scoring Matrix**:
```
Severity × Probability = Risk Level

Severity:
- Low: <$5,000 impact
- Medium: $5,000-50,000 impact
- High: >$50,000 impact

Probability:
- Unlikely: <20% chance
- Possible: 20-60% chance
- Likely: >60% chance

Risk Level:
- Critical: High severity + Likely probability
- High: High severity + Possible, or Medium severity + Likely
- Medium: Medium severity + Possible, or Low severity + Likely
- Low: Low severity + Unlikely
```

### Step 3: Compliance Review
Check regulatory requirements specific to industry and geography.

**Compliance Checklist**:
- [ ] Data privacy (GDPR, CCPA, LGPD)
- [ ] Financial regulations (PCI-DSS if handling payments)
- [ ] Healthcare (HIPAA if health data)
- [ ] Education (FERPA if student data)
- [ ] Children's privacy (COPPA if under 13)
- [ ] Accessibility (ADA, WCAG if public-facing)
- [ ] Export controls (ITAR, EAR if sensitive tech)
- [ ] Industry-specific (SEC for finance, FDA for medical devices)

### Step 4: Mitigation Planning
Propose specific risk reduction strategies.

**Mitigation Strategies**:
- Preventive controls (stop risk from occurring)
- Detective controls (identify risk quickly)
- Corrective controls (minimize damage after occurrence)
- Transfer strategies (insurance, vendor warranties)
- Acceptance strategies (acknowledge and plan for risk)

### Step 5: Monitoring Framework
Define KPIs and early warning indicators.

**Key Metrics to Track**:
- Daily API costs vs. budget
- User growth rate vs. infrastructure capacity
- Monthly churn rate
- Customer acquisition cost (CAC)
- Error rates and downtime incidents
- Compliance audit findings

## Risk Mitigation Strategies

### Regulatory Compliance

**GDPR Mitigation**:
```
Actions:
1. Implement data minimization (collect only necessary data)
2. Add user consent mechanisms (checkboxes, opt-in)
3. Provide data export/deletion features
4. Conduct Data Protection Impact Assessment (DPIA)
5. Appoint Data Protection Officer (if required)
6. Update privacy policy with legal review

Cost: $5,000-20,000 (consultant) + $2,000-5,000 (legal review)
Timeline: 2-3 months
Priority: HIGH (before launching in EU)
```

**HIPAA Mitigation**:
```
Actions:
1. Encrypt data at rest and in transit
2. Implement access controls and audit logs
3. Sign Business Associate Agreements (BAAs) with vendors
4. Conduct annual risk assessments
5. Train team on HIPAA requirements
6. Develop incident response plan

Cost: $10,000-30,000 (initial setup) + $5,000/year (ongoing)
Timeline: 3-6 months
Priority: CRITICAL (before handling health data)
```

**SOC2 Mitigation**:
```
Actions:
1. Implement security controls (2FA, encryption, logging)
2. Document policies and procedures
3. Conduct readiness assessment
4. Hire SOC2 auditor
5. Remediate findings
6. Maintain evidence collection

Cost: $15,000-50,000 (initial audit) + $10,000-25,000/year (recurring)
Timeline: 4-8 months
Priority: HIGH (for enterprise sales)
```

### Cost Overrun Prevention

**API Usage Spike Mitigation**:
```
Actions:
1. Implement rate limiting per user (e.g., 100 requests/hour)
2. Set up cost alerts at 80% of budget threshold
3. Add usage caps with soft/hard limits
4. Implement caching for repeated requests
5. Use exponential backoff for retries
6. Monitor for bot traffic and abuse patterns

Cost: $2,000-5,000 (development time)
Savings: Prevents $5,000-50,000+ in unexpected API charges
Priority: HIGH
```

**Infrastructure Scaling Mitigation**:
```
Actions:
1. Use auto-scaling with maximum capacity limits
2. Implement reserved instances for baseline load
3. Set up cost anomaly detection
4. Use spot instances for batch workloads
5. Implement graceful degradation for peak traffic
6. Plan capacity with 2-3 month lead time

Cost: $3,000-8,000 (DevOps time)
Savings: 20-35% reduction in infrastructure costs
Priority: MEDIUM (before scaling phase)
```

### Integration Risk Mitigation

**Vendor Lock-in Prevention**:
```
Actions:
1. Use abstraction layers for critical services
2. Maintain data export capabilities
3. Evaluate multi-vendor strategies for critical path
4. Review vendor contract terms (price lock, SLAs)
5. Document migration procedures
6. Test disaster recovery plans

Cost: $5,000-15,000 (architectural planning and implementation)
Benefit: Flexibility to switch vendors, negotiate better pricing
Priority: MEDIUM (before deep integration)
```

**API Deprecation Mitigation**:
```
Actions:
1. Subscribe to vendor API changelog notifications
2. Version all integrations explicitly
3. Maintain fallback options for critical features
4. Budget 10-20% time for integration maintenance
5. Join vendor developer communities
6. Review vendor roadmap quarterly

Cost: 2-4 hours/week ongoing maintenance
Benefit: Avoid emergency migration costs ($20,000-100,000+)
Priority: HIGH (for all third-party integrations)
```

### Revenue Risk Mitigation

**Churn Reduction**:
```
Actions:
1. Implement usage analytics to identify at-risk users
2. Add in-app onboarding and education
3. Provide proactive customer support
4. Offer annual discounts (reduce monthly churn)
5. Conduct exit surveys to understand reasons
6. Build retention features (saved preferences, history)

Cost: $10,000-30,000 (development and support)
Impact: Reducing churn from 10% to 5% doubles customer lifetime value
Priority: HIGH (for subscription businesses)
```

**Pricing Model Optimization**:
```
Actions:
1. Analyze usage patterns by customer segment
2. Test multiple pricing tiers (A/B testing)
3. Align pricing with value delivered (not just costs)
4. Implement usage-based components for variable load
5. Offer annual prepay discounts (improve cash flow)
6. Review pricing quarterly based on data

Cost: $5,000-15,000 (analysis and implementation)
Impact: 10-30% revenue increase from optimized pricing
Priority: MEDIUM (after initial traction)
```

## Risk Matrix Template

Use this template to document identified risks:

| Risk Description | Category | Severity | Probability | Financial Impact | Mitigation Strategy | Status |
|------------------|----------|----------|-------------|------------------|---------------------|---------|
| GDPR non-compliance fine | Regulatory | High | Possible | €20M or 4% revenue | Implement GDPR compliance program | In Progress |
| Claude API cost spike | Cost Overrun | High | Likely | +$10k-50k/month | Rate limiting, usage caps, monitoring | Planned |
| Stripe price increase | Integration | Low | Possible | +$200-500/month | Budget buffer, consider alternatives | Accepted |
| High customer churn | Revenue | Medium | Possible | -$5k-20k/month | Improve onboarding, add retention features | In Progress |

## Common Financial Risks by Project Type

### SaaS Application

**Top Risks**:
1. High customer churn (>5% monthly)
2. API costs scaling faster than revenue
3. SOC2 compliance required for enterprise sales
4. Payment processor fees eroding margins
5. Customer acquisition cost exceeding lifetime value

**Recommended Focus**: Revenue sustainability and compliance

### API Service

**Top Risks**:
1. Rate limit abuse driving costs
2. Pricing model misaligned with costs (giving away value)
3. Vendor API deprecation or price increases
4. DDoS attacks increasing infrastructure costs
5. Free tier abuse without conversion

**Recommended Focus**: Cost control and pricing optimization

### Open Source Project

**Top Risks**:
1. Maintainer burnout (unpaid labor unsustainable)
2. Lack of sponsorship/funding
3. Enterprise users without financial contribution
4. Infrastructure costs (CI/CD, hosting) without revenue
5. Legal liability without corporate backing

**Recommended Focus**: Sustainability and legal protection

### Mobile App

**Top Risks**:
1. App store fees (30% of revenue)
2. Payment processing on top of store fees
3. Platform changes breaking functionality
4. High user acquisition costs ($2-10+ per install)
5. Freemium model with low conversion (<2%)

**Recommended Focus**: Unit economics and acquisition efficiency

## Monitoring and Early Warning

### Daily Metrics
- API cost per active user
- Error rates by endpoint
- Infrastructure utilization vs. capacity
- Payment success rate

### Weekly Metrics
- Customer churn rate
- New user activation rate
- Revenue per user
- Support ticket volume

### Monthly Metrics
- Customer Acquisition Cost (CAC)
- Customer Lifetime Value (LTV)
- Gross margin %
- Burn rate (for startups)

### Quarterly Metrics
- SOC2/compliance audit status
- Third-party vendor price changes
- Competitive pricing analysis
- Technical debt assessment

### Alert Thresholds

Set automated alerts for:
```
CRITICAL:
- Daily costs exceed 150% of budget
- Error rate >1% (potential security issue)
- Payment processor downtime >5 minutes
- Data breach detected

HIGH:
- Daily costs exceed 125% of budget
- Churn rate increases 50% week-over-week
- API vendor announces deprecation
- Compliance audit finding

MEDIUM:
- Daily costs exceed 110% of budget
- Support ticket volume doubles
- Free tier usage spikes without conversion
- Infrastructure at 80% capacity
```

## Integration with Other Skills

- **cost-estimation**: Use cost estimates to baseline risk impact
- **monetization-planning**: Ensure pricing covers identified financial risks
- **roi-analysis**: Include risk factors in ROI calculations

## Examples

### Example 1: SaaS Startup Risk Assessment

**Project**: B2B SaaS with Claude AI features
**Revenue**: Pre-revenue, launching in 3 months
**Team**: 3 developers, bootstrapped

**Critical Risks Identified**:

1. **API Cost Overrun** (HIGH RISK)
   - Severity: High ($20k+ potential monthly cost)
   - Probability: Likely (no usage caps implemented)
   - Impact: Could exhaust runway in 2-3 months
   - Mitigation: Implement rate limiting BEFORE launch

2. **SOC2 Non-compliance** (MEDIUM RISK)
   - Severity: High (lose enterprise deals worth $100k+)
   - Probability: Possible (no SOC2 controls in place)
   - Impact: Can't sell to Fortune 500 customers
   - Mitigation: Start SOC2 readiness now (4-6 month timeline)

3. **GDPR Non-compliance** (HIGH RISK)
   - Severity: High (€20M or 4% revenue fine)
   - Probability: Possible (targeting EU customers)
   - Impact: Regulatory fine + reputation damage
   - Mitigation: GDPR compliance before EU launch

**Recommendation**: Delay launch by 1 month to implement critical mitigations (rate limiting, basic GDPR compliance). Start SOC2 process in parallel.

### Example 2: API Service Risk Assessment

**Project**: AI image generation API
**Revenue**: $50k MRR, 5,000 API customers
**Team**: 5 engineers, funded

**Critical Risks Identified**:

1. **Vendor API Price Increase** (MEDIUM RISK)
   - Severity: Medium ($5-10k monthly increase)
   - Probability: Likely (vendor history of 30% annual increases)
   - Impact: Margin compression from 40% to 25%
   - Mitigation: Pass-through pricing clause in contracts, evaluate alternatives

2. **Free Tier Abuse** (HIGH RISK)
   - Severity: Medium ($5-15k monthly cost)
   - Probability: Likely (currently experiencing abuse)
   - Impact: Serving unprofitable traffic
   - Mitigation: Stricter rate limits, CAPTCHA, require credit card

3. **Rate Limit Ceiling** (LOW RISK)
   - Severity: Low (need to upgrade vendor tier +$2k/month)
   - Probability: Possible (growing 20% monthly)
   - Impact: Growth constrained by rate limits
   - Mitigation: Budget for tier upgrade in Q2, negotiate custom pricing

**Recommendation**: Implement free tier abuse prevention immediately. Negotiate vendor pricing for annual commit (10-20% discount).

## Tips and Best Practices

1. **Assess risks quarterly** - Financial landscape changes rapidly
2. **Quantify everything** - Vague risks don't get mitigated
3. **Prioritize by expected value** - Severity × Probability = Priority
4. **Don't ignore low-probability/high-severity risks** - "Black swans" can kill projects
5. **Compliance is not optional** - Budget for it from day one
6. **Monitor leading indicators** - Don't wait for the crisis
7. **Insurance for critical risks** - Cybersecurity insurance, E&O insurance
8. **Document everything** - Auditors and investors will ask
9. **Test incident response** - Have a plan before the emergency
10. **Build in buffers** - 20-30% cost buffer for risk mitigation

## Limitations

- Risk probabilities are estimates, not guarantees
- Regulatory landscape changes (monitor for updates)
- Doesn't cover all edge cases (black swan events)
- Financial impacts are approximate
- Mitigation strategies have their own costs and risks
- Requires ongoing monitoring and updates

## Version History

- **1.0.0** (January 2025): Initial release with 5-step framework

## Related Resources

- [Financial Advisor Agent](../../agents/financial-advisor/README.md)
- [Financial Risk Audit Command](../../commands/financial-risk-audit.md)
- [Cost Estimation Skill](../cost-estimation/README.md)
