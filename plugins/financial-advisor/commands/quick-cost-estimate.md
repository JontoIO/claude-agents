# Quick Cost Estimate Command

Provides a rapid cost estimate for a specific feature, component, or project without conducting a full cost analysis.

## Purpose

Get a quick ballpark cost estimate when:
- Evaluating whether to build vs buy a feature
- Deciding between architectural options
- Planning sprint priorities based on cost impact
- Responding to stakeholder questions about costs
- Making fast go/no-go decisions

## When to Use

**Use quick-cost-estimate when**:
- Need estimate in minutes, not hours
- Rough accuracy (±30-40%) is acceptable
- Evaluating a specific feature or component
- Comparing relative costs of options
- Early stage idea validation

**Use full cost-estimation skill when**:
- Need detailed accuracy (±20%)
- Planning full project budget
- Presenting to investors or board
- Making major financial commitments
- Require comprehensive breakdown

## Command Format

```bash
/quick-cost-estimate [feature/component description]
```

### Optional Parameters

Add context to improve estimate accuracy:

```
--users [number]         Expected number of users
--api-calls [number]     API calls per user per day
--tokens [number]        Tokens per API call
--timeline [duration]    Development timeline (weeks/months)
--team [composition]     Team makeup (e.g., "2 devs, 1 designer")
--stack [technologies]   Tech stack if relevant
```

## Examples

### Example 1: Basic Feature Estimate

```bash
/quick-cost-estimate Add AI-powered content summarization feature
```

**Expected Output**:
```
Quick Cost Estimate: AI Content Summarization

Development:
- Backend API integration: 40-60 hours
- Frontend UI: 20-30 hours
- Testing & refinement: 20-30 hours
Total: 80-120 hours @ $100/hr avg = $8,000-12,000 one-time

Monthly Operational Costs:
- Claude API (assuming 1,000 users, 10 summaries/user/day):
  * 1,000 users × 10 calls × 500 tokens × $15/1M × 30 days
  * = $2,250/month
- Infrastructure: negligible increase (use existing)
Total: ~$2,300/month

Break-even: Need $0.08/user/month revenue to cover API costs

Accuracy: ±40% (use full cost-estimation for detailed planning)
Assumptions: 500 tokens per summary, Claude 3.5 Sonnet output pricing
```

### Example 2: With Parameters

```bash
/quick-cost-estimate Add real-time collaboration feature --users 5000 --team "3 senior devs, 1 DevOps" --timeline "3 months"
```

**Expected Output**:
```
Quick Cost Estimate: Real-time Collaboration

Development (3 months):
- 3 Senior Developers: 3 × $100/hr × 480 hrs = $144,000
- 1 DevOps Engineer: 1 × $90/hr × 240 hrs = $21,600
Total Development: $165,600

Infrastructure (monthly at 5,000 users):
- WebSocket servers (2× AWS c5.large): $140
- Redis for real-time state: $50
- Increased bandwidth: $100
Total Infrastructure: $290/month

Third-party Services:
- Consider: Pusher ($499/month), Ably ($399/month), or self-host
- Estimate: $400/month for managed service

Total Monthly Operational: ~$700/month

Total Project Cost: $165,600 + ($700 × 3) = $167,700 over 3 months

Ongoing: $700/month after launch

Accuracy: ±35%
Key Assumption: WebSocket connections average 15 minutes per session
Alternative: Use Pusher/Ably to reduce dev cost to $50k but increase monthly to $700
```

### Example 3: Build vs Buy Decision

```bash
/quick-cost-estimate Build custom authentication vs using Auth0 --users 1000
```

**Expected Output**:
```
Quick Cost Estimate: Auth System Comparison

Option A: Build Custom
Development:
- User model & database: 20 hrs
- Login/signup flows: 40 hrs
- Password reset: 16 hrs
- Email verification: 16 hrs
- OAuth providers (Google, GitHub): 40 hrs
- 2FA implementation: 32 hrs
- Security hardening: 24 hrs
Total: 188 hours @ $100/hr = $18,800 one-time

Maintenance: 10 hrs/month @ $100/hr = $1,000/month

Infrastructure: $50/month (email service)

Option B: Auth0
Development:
- Integration: 20 hrs @ $100/hr = $2,000 one-time
Monthly Cost: $35 (Essentials) + (1,000 users × $0.05) = $85/month

Cost Comparison:
Year 1: Custom = $30,800, Auth0 = $3,020
Year 2: Custom = $12,000, Auth0 = $1,020
Year 3: Custom = $12,000, Auth0 = $1,020

Break-even: Never (Auth0 is cheaper at this scale)

Recommendation: Use Auth0 unless:
- Users >20,000 (custom becomes cheaper)
- Highly custom auth requirements
- Regulatory need for full control

Accuracy: ±30%
```

### Example 4: API Cost Estimate

```bash
/quick-cost-estimate Claude API costs --users 10000 --api-calls 50 --tokens 1500
```

**Expected Output**:
```
Quick Cost Estimate: Claude API Costs

Usage Pattern:
- 10,000 users
- 50 API calls per user per day
- 1,500 tokens per call (assuming 60% input, 40% output)

Monthly Cost Calculation:
Input tokens: 10,000 × 50 × 1,500 × 0.6 × 30 = 13.5B tokens
Input cost: 13,500M tokens × $3/M = $40,500

Output tokens: 10,000 × 50 × 1,500 × 0.4 × 30 = 9B tokens
Output cost: 9,000M tokens × $15/M = $135,000

Total Monthly: $175,500

Cost per user: $17.55/month
Cost per API call: $0.35

Optimization Opportunities:
- Prompt caching (20% savings): -$35,100 → $140,400/month
- Reduce tokens 20% via prompt engineering: -$35,100 → $140,400/month
- Use Claude 3 Haiku for simple requests (95% cheaper): Varies by mix

With both optimizations: ~$105,000/month (40% savings)

Pricing Tier Recommendation:
- Contact Anthropic enterprise sales for volume pricing
- Expect 15-30% discount at this volume

Accuracy: ±25% (actual may vary with usage patterns)
Pricing: As of January 2025
```

### Example 5: Infrastructure Scaling

```bash
/quick-cost-estimate Scale infrastructure from 1,000 to 10,000 users --stack "Node.js, PostgreSQL, AWS"
```

**Expected Output**:
```
Quick Cost Estimate: Infrastructure Scaling (10x users)

Current (1,000 users):
- App servers: 2× t3.medium = $40/month
- Database: db.t3.small = $25/month
- Load balancer: $16/month
- S3 storage: 100GB = $2/month
Total: ~$85/month

Target (10,000 users):
- App servers: 5× t3.large (auto-scale) = $200/month
- Database: db.m5.large + read replica = $280/month
- Load balancer: $16/month (same)
- S3 storage: 1TB = $23/month
- CloudFront CDN: 500GB transfer = $43/month
- Backup & monitoring: $50/month
Total: ~$612/month

Cost increase: $527/month (7.2x)
Cost per user:
- Current: $0.085/user/month
- Target: $0.061/user/month (economies of scale)

DevOps effort to scale:
- Auto-scaling setup: 20 hrs
- Database migration: 16 hrs
- CDN configuration: 8 hrs
- Load testing: 16 hrs
Total: 60 hours @ $90/hr = $5,400 one-time

Total Scaling Cost: $5,400 + $527/month ongoing

Note: Costs scale non-linearly. 10x users ≠ 10x infrastructure.

Accuracy: ±35%
Recommendation: Use reserved instances for 35% savings on predictable load
```

## Estimation Methodology

The command uses simplified formulas for speed:

### Development Time Estimation

```
Simple feature: 40-80 hours
Medium feature: 80-160 hours
Complex feature: 160-400 hours
Major feature/module: 400-1000+ hours

Multiply by average hourly rate ($80-120/hr typical)
```

### API Cost Estimation

```
Monthly Cost = Users × Calls/User/Day × Tokens/Call × Price/M tokens × 30 / 1,000,000

Default assumptions if not specified:
- Calls/user/day: 10
- Tokens/call: 1,000 (60% input, 40% output)
- Price: Claude 3.5 Sonnet ($3 input, $15 output per 1M tokens)
```

### Infrastructure Estimation

```
Baseline AWS costs:
- Small app (100-1k users): $50-200/month
- Medium app (1k-10k users): $200-1,000/month
- Large app (10k-100k users): $1,000-5,000/month
- Enterprise (100k+ users): $5,000+ (needs custom estimate)

Scale approximately with log(users) not linear
```

### Maintenance Estimation

```
Ongoing maintenance: 10-20% of initial development cost per year
Example: $50k build → $5k-10k/year maintenance
```

## Output Format

Every quick estimate includes:

1. **Cost Breakdown**
   - One-time costs (development)
   - Monthly recurring costs (operational)
   - Clearly separated

2. **Key Assumptions**
   - What was assumed to reach the estimate
   - What variables have biggest impact

3. **Accuracy Note**
   - Typical range: ±30-40%
   - Note when full cost-estimation recommended

4. **Actionable Insight**
   - Break-even point
   - Build vs buy recommendation
   - Optimization opportunities
   - When to proceed vs get more data

## Limitations

**Quick estimate is NOT suitable for**:
- Board presentations or investor pitches
- Contract negotiations
- Detailed budget planning
- Compliance cost assessment
- Multi-year financial projections

**Accuracy factors**:
- ±30-40% typical
- Better for operational costs (APIs, infrastructure)
- Worse for custom development (high variability)
- Assumes industry-standard rates and patterns

## Improving Accuracy

To get closer to ±20% accuracy:

1. **Provide more context**: The more parameters you specify, the better
2. **Reference similar features**: "Like the export feature we built"
3. **Specify constraints**: "Must be HIPAA compliant" changes estimate significantly
4. **Use full cost-estimation**: When accuracy matters, take the extra time

## Common Use Cases

### Sprint Planning
```bash
/quick-cost-estimate Add PDF export feature
# Compare cost vs sprint capacity and user value
```

### Technical Debt Decision
```bash
/quick-cost-estimate Refactor authentication system
# Decide if technical debt is worth paying down now
```

### Build vs Buy
```bash
/quick-cost-estimate Build custom CMS vs use Contentful
# Compare total cost of ownership
```

### Scaling Decision
```bash
/quick-cost-estimate Move from monolith to microservices --users 50000
# Evaluate if scale justifies architectural change
```

### Feature Prioritization
```bash
/quick-cost-estimate Add social login
/quick-cost-estimate Add dark mode
/quick-cost-estimate Add export to Excel
# Compare costs to prioritize roadmap
```

## Tips for Better Estimates

1. **Be specific**: "Add AI chat" vs "Add AI chat with conversation history, streaming, and user feedback"

2. **Specify scale**: Costs vary wildly between 100 and 100,000 users

3. **Include constraints**: "HIPAA compliant" or "Sub-100ms latency" increase costs

4. **Compare options**: Ask for estimates of multiple approaches

5. **Validate assumptions**: Check if default assumptions match your case

6. **Follow up**: If estimate is critical, follow with full cost-estimation skill

## Integration with Other Skills

- **cost-estimation**: Use for detailed breakdown after quick estimate shows promise
- **roi-analysis**: Use quick estimate as input to ROI calculation
- **financial-risk-assessment**: Quick estimate helps identify cost overrun risks

## Related Commands

- `/cost-estimation` - Full detailed cost analysis
- `/monetization-strategy-review` - Evaluate revenue needed to cover estimated costs
- `/financial-risk-audit` - Identify risks in cost assumptions

---

**Remember**: Quick estimates trade accuracy for speed. Use them for fast decisions, but validate with detailed analysis before major commitments.
