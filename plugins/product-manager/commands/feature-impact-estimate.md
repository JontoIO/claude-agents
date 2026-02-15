# Feature Impact Estimate Command

Generates a quick RICE score and go/no-go recommendation in 3-5 minutes for fast feature prioritization decisions.

## Purpose

Get a quick impact estimate when:
- Prioritizing features on roadmap
- Making fast build vs defer decisions
- Comparing multiple feature options
- Need quick justification for stakeholders
- Evaluating feature requests

## When to Use

**Use feature-impact-estimate when**:
- Need estimate in 3-5 minutes
- Rough prioritization is sufficient
- Comparing 2-5 features quickly
- Making sprint planning decisions
- Responding to "should we build this?" questions

**Use full improvement-proposals skill when**:
- Need detailed PRD
- Comprehensive impact analysis required
- Building business case for stakeholders
- Complex feature with dependencies
- Presenting to leadership for approval

## Command Format

```bash
/feature-impact-estimate [feature description]
```

### Optional Parameters

Add context to improve estimate accuracy:

```
--reach [number]         Estimated users affected per quarter
--impact [score]         Impact per user: 3=massive, 2=high, 1=medium, 0.5=low, 0.25=minimal
--confidence [percent]   Confidence in estimate (0-100%)
--effort [weeks]         Development effort in person-weeks
--context [details]      Additional context (target users, constraints, etc.)
```

## RICE Framework Quick Reference

```
RICE Score = (Reach × Impact × Confidence) / Effort

Reach: How many users per quarter?
Impact: How much does it help each user? (0.25 to 3)
Confidence: How sure are you? (0-100%)
Effort: How many person-weeks to build?

Higher RICE = Higher Priority
```

## Examples

### Example 1: Basic Feature Estimate

```bash
/feature-impact-estimate Add export to PDF feature
```

**Expected Output**:
```
Feature Impact Estimate: Export to PDF

RICE Score: 48
Priority: HIGH - Recommended to build

RICE Breakdown:
┌────────────┬────────┬─────────────────────────────┐
│ Component  │ Score  │ Reasoning                   │
├────────────┼────────┼─────────────────────────────┤
│ Reach      │ 2,000  │ 40% of users (5k total)    │
│            │        │ export monthly             │
├────────────┼────────┼─────────────────────────────┤
│ Impact     │ 2.0    │ High - solves major pain   │
│            │        │ Users currently copy/paste │
│            │        │ Reduces 10min to 10sec     │
├────────────┼────────┼─────────────────────────────┤
│ Confidence │ 80%    │ Medium-high                │
│            │        │ - Clear user requests (✓)  │
│            │        │ - Standard feature (✓)     │
│            │        │ - Tech validated (✓)       │
│            │        │ - Effort estimate (?)      │
├────────────┼────────┼─────────────────────────────┤
│ Effort     │ 2 weeks│ ~80 hours total            │
│            │        │ - Backend PDF gen: 40h     │
│            │        │ - UI/download: 20h         │
│            │        │ - Testing: 20h             │
└────────────┴────────┴─────────────────────────────┘

RICE Calculation:
(2,000 × 2.0 × 0.80) / 2 = 1,600 per week effort
                         = 48 (quarterly score)

Impact Analysis:

User Value:
✓ Highly requested (10+ support tickets/month)
✓ Competitors have it (table stakes)
✓ Clear use case (sharing, printing, archiving)
✓ Reduces workaround time by ~10 min per export

Business Value:
✓ Reduces support burden (copy/paste issues)
✓ Increases perceived professionalism
✓ May improve conversion (expected feature)
⚠ Unlikely to drive new user acquisition

Risks:
⚠ PDF formatting can be tricky (edge cases)
⚠ File size concerns with large documents
⚠ Cross-browser compatibility testing needed

Recommendation: BUILD IT

Why build now:
• High user demand (2,000 users/quarter need it)
• Reasonable effort (2 weeks)
• Strong RICE score (48) beats most backlog items
• Table stakes feature (competitors have it)
• Clear success metrics (adoption, support ticket reduction)

Success Metrics:
- 40%+ of users export to PDF within 3 months
- Support tickets about sharing decrease 30%
- No major PDF rendering bugs reported
- <5 second generation time for typical docs

Time to generate: 4 minutes
For detailed PRD: Use /improvement-proposals skill
```

### Example 2: With Parameters Specified

```bash
/feature-impact-estimate Add real-time collaboration --reach 5000 --impact 3 --effort 12 --confidence 60
```

**Expected Output**:
```
Feature Impact Estimate: Real-time Collaboration

RICE Score: 75
Priority: VERY HIGH - Strong candidate for roadmap

RICE Breakdown:
┌────────────┬────────┬─────────────────────────────┐
│ Component  │ Score  │ Details                     │
├────────────┼────────┼─────────────────────────────┤
│ Reach      │ 5,000  │ (provided)                 │
│            │        │ ~100% of users will benefit│
├────────────┼────────┼─────────────────────────────┤
│ Impact     │ 3.0    │ Massive (provided)         │
│            │        │ Transforms how users work  │
│            │        │ Major competitive advantage│
├────────────┼────────┼─────────────────────────────┤
│ Confidence │ 60%    │ Medium (provided)          │
│            │        │ - User demand: High        │
│            │        │ - Tech complexity: High    │
│            │        │ - Scope uncertainty: Yes   │
├────────────┼────────┼─────────────────────────────┤
│ Effort     │ 12 wks │ (provided)                 │
│            │        │ Significant investment     │
└────────────┴────────┴─────────────────────────────┘

RICE Calculation:
(5,000 × 3.0 × 0.60) / 12 = 750 per week effort
                           = 75 (quarterly score)

Impact Analysis:

User Value:
✓ Major workflow improvement (3x impact)
✓ Enables new use cases (team collaboration)
✓ Competitive differentiator
✓ May reduce other tools (consolidation)

Business Value:
✓ Potential revenue impact (upsell opportunity)
✓ User retention (sticky feature)
✓ Competitive advantage
✓ Marketing/PR value

Risks & Uncertainties:
⚠ 60% confidence = significant unknowns
⚠ 12 weeks is major commitment
⚠ Technical complexity (sync, conflicts, scale)
⚠ Scope creep risk (features within feature)
⚠ May need additional infrastructure costs

Confidence Breakdown:
Why only 60%:
- Technical feasibility validated but complex
- Effort estimate based on high-level design
- Unclear which collab features are MVP
- Performance at scale needs validation
- User adoption rate uncertain

To increase confidence:
→ Technical spike (2 weeks) to validate approach
→ User interviews to prioritize collab features
→ Prototype with 10 beta users
→ Detailed design doc with edge cases

Recommendation: INVESTIGATE FURTHER, THEN BUILD

Why not "build immediately":
• 60% confidence too low for 12-week commitment
• Need spike to reduce uncertainty
• Scope definition will affect effort significantly

Suggested path:
1. Week 1-2: Technical spike + user research
2. Week 3: Refine scope and effort estimate
3. Week 4: Build or defer decision with higher confidence

If confidence increases to 80%+, RICE jumps to 100 → top priority

Success Metrics:
- 60%+ of teams use real-time collab within 6 months
- 30%+ reduction in async comments
- <500ms sync latency p95
- Zero data loss incidents
- 80%+ user satisfaction with performance

Time to generate: 5 minutes
For detailed PRD: Use /improvement-proposals skill
```

### Example 3: Comparing Multiple Features

```bash
/feature-impact-estimate Dark mode
/feature-impact-estimate Keyboard shortcuts
/feature-impact-estimate Mobile app
```

**Expected Output (Combined)**:
```
Feature Impact Comparison

Ranked by RICE Score:

1. Mobile App - RICE: 64 (VERY HIGH) ✓✓✓
   Reach: 4,000 | Impact: 2.0 | Confidence: 80% | Effort: 10 weeks
   Recommendation: BUILD NEXT QUARTER

   Why it's top:
   • High reach (80% of users want mobile access)
   • Clear impact (work anywhere = 2x usage)
   • Proven effort estimate (10 weeks standard)
   • Strong confidence (validated demand)

   Key consideration:
   - Major investment (10 weeks)
   - Requires mobile expertise
   - Ongoing maintenance burden

   Success criteria:
   - 50%+ users adopt mobile within 3 months
   - 4.0+ star rating in app stores
   - 20%+ increase in daily active users

---

2. Keyboard Shortcuts - RICE: 42 (HIGH) ✓✓
   Reach: 3,000 | Impact: 1.0 | Confidence: 90% | Effort: 3 weeks
   Recommendation: BUILD SOON

   Why it's strong:
   • High confidence (clear scope, known effort)
   • Reasonable effort (3 weeks)
   • Good reach (60% of users are power users)
   • Low risk

   Key consideration:
   - "Nice-to-have" vs mobile is "must-have"
   - Can build faster than mobile
   - Smaller impact per user

   Success criteria:
   - 30%+ of users use shortcuts weekly
   - 10 most common actions have shortcuts
   - Discoverability >50% (users know shortcuts exist)

---

3. Dark Mode - RICE: 18 (MEDIUM) ✓
   Reach: 3,000 | Impact: 0.5 | Confidence: 95% | Effort: 4 weeks
   Recommendation: DEFER OR BUILD LATER

   Why it's lower priority:
   • Low impact per user (nice-to-have, not transformative)
   • Effort seems high for impact delivered
   • Other features provide more value

   Key consideration:
   - Highly requested but low actual impact
   - Can be quick win IF effort is 1-2 weeks
   - May improve perceived quality

   When to reconsider:
   → If effort drops to 1-2 weeks (RICE → 28-57)
   → If part of larger design system work
   → If no higher RICE items in backlog

   Success criteria:
   - 40%+ users enable dark mode
   - <5 reported UI bugs
   - No performance impact

Priority Matrix:
┌──────────────────┬───────┬────────┬────────────┬────────────┐
│ Feature          │ RICE  │ Reach  │ Impact     │ Effort     │
├──────────────────┼───────┼────────┼────────────┼────────────┤
│ Mobile App       │  64   │ 4,000  │ 2.0 (High) │ 10 weeks   │
│ Keyboard Shortcuts│  42   │ 3,000  │ 1.0 (Med)  │ 3 weeks    │
│ Dark Mode        │  18   │ 3,000  │ 0.5 (Low)  │ 4 weeks    │
└──────────────────┴───────┴────────┴────────────┴────────────┘

Recommendation:
Q2: Mobile App (64)
Q3: Keyboard Shortcuts (42)
Q4+: Dark Mode (18) if no better options

Quick wins (if time):
- Keyboard Shortcuts (3 weeks, RICE 42) before Mobile App starts
- Allows parallel work if resources available

Time to generate: 5 minutes (all 3)
For detailed PRD: Use /improvement-proposals skill
```

### Example 4: Feature Request Evaluation

```bash
/feature-impact-estimate Add custom fields requested by Enterprise customer --context "Customer paying $50k/year, threatening to churn"
```

**Expected Output**:
```
Feature Impact Estimate: Custom Fields (Enterprise Request)

RICE Score: 35
Priority: HIGH (with context)

RICE Breakdown:
┌────────────┬────────┬─────────────────────────────┐
│ Component  │ Score  │ Analysis                    │
├────────────┼────────┼─────────────────────────────┤
│ Reach      │ 500    │ Enterprise customers only  │
│            │        │ 10 customers × 50 users     │
│            │        │ May expand to SMB later     │
├────────────┼────────┼─────────────────────────────┤
│ Impact     │ 2.0    │ High for enterprise        │
│            │        │ Blocker for adoption       │
│            │        │ Workflow customization     │
├────────────┼────────┼─────────────────────────────┤
│ Confidence │ 70%    │ Medium-high                │
│            │        │ - 1 customer validated (✓) │
│            │        │ - Others may want (?)      │
│            │        │ - Scope creep risk (⚠)    │
├────────────┼────────┼─────────────────────────────┤
│ Effort     │ 4 weeks│ Estimated effort           │
│            │        │ - Data model: 1 week       │
│            │        │ - UI builder: 2 weeks      │
│            │        │ - Testing: 1 week          │
└────────────┴────────┴─────────────────────────────┘

RICE Calculation:
(500 × 2.0 × 0.70) / 4 = 175 per week effort
                       = 35 (quarterly score)

Context Considerations:

Customer Risk:
🚨 $50k/year customer threatening churn
   • Annual value: $50,000
   • Lifetime value: ~$200k (4 years avg)
   • Development cost: ~$40k (4 weeks @ $100/hr)
   • ROI: 5:1 if prevents churn

But also consider:
⚠ One customer ≠ market validation
⚠ Custom features can become support burden
⚠ May not generalize to other customers
⚠ Technical debt if done quickly

Strategic Value:

Enterprise Play:
✓ Signals enterprise-ready
✓ May unlock other large deals
✓ Custom fields = common enterprise ask
✓ Can be part of Enterprise tier upsell

SMB Applicability:
⚠ Unknown if SMBs need this (low confidence)
⚠ May add complexity for simple use cases
⚠ Could confuse/overwhelm small teams

Recommendation: BUILD, BUT VALIDATE FIRST

Action Plan:

Week 1: Validation (CRITICAL)
□ Interview 5 other enterprise customers
  → Do they need custom fields?
  → What fields specifically?
  → What's their priority?
□ Check competitor offerings
  → Is this table stakes?
  → How do they implement it?
□ Design lightweight MVP scope
  → What's minimum to prevent churn?
  → What can wait for v2?

Week 2-5: Build (IF VALIDATED)
□ Implement MVP version
□ Beta with requesting customer
□ Iterate based on feedback

Alternative: Buy Time
If validation unclear:
→ Offer manual workaround (support team helps)
→ Extend contract negotiation (discount for 90 days)
→ Prototype with requesting customer
→ Validate broader need before full build

Risk Analysis:

If we BUILD:
✓ Save $50k customer
✓ Make enterprise offering stronger
⚠ 4 weeks investment
⚠ May only serve one customer
⚠ Ongoing maintenance

If we DON'T BUILD:
⚠ Lose $50k/year customer
⚠ Signal we're not enterprise-ready
✓ Can focus on higher RICE features
✓ Avoid niche feature debt

Adjusted Priority:
Pure RICE: 35 (Medium)
With context: HIGH (churn risk)

Recommendation: BUILD if validation confirms broader need

Validation targets:
- 3+ of 10 enterprise customers want it
- At least 1 other customer willing to pay for it
- Feature appears in 30%+ of competitor offerings

Success Metrics:
- Customer renews contract
- 5+ other enterprise customers adopt custom fields
- <10 support tickets about the feature
- No performance degradation
- 70%+ of enterprise users create custom fields

Time to generate: 5 minutes
For detailed PRD: Use /improvement-proposals skill
For cost analysis: Use /quick-cost-estimate command
```

### Example 5: Technical Debt vs Feature

```bash
/feature-impact-estimate Refactor authentication system to OAuth 2.0 --context "Current system has security vulnerabilities and tech debt"
```

**Expected Output**:
```
Feature Impact Estimate: OAuth 2.0 Migration (Tech Debt)

RICE Score: N/A (Tech debt different model)
Priority: HIGH - Technical necessity

Note: RICE works poorly for technical debt. Using modified framework.

Impact Assessment:

User-Facing Impact: ⚠ LOW (mostly invisible)
- Users won't notice the change
- Login flow remains similar
- Potential for SSO later (future value)

Technical Impact: ✓✓✓ VERY HIGH
- Fixes security vulnerabilities
- Enables future features (SSO, OAuth providers)
- Reduces maintenance burden
- Industry standard (easier to hire, maintain)

Business Impact: ✓✓ HIGH
- Security risk mitigation (critical)
- Compliance (SOC 2 may require it)
- Enables enterprise sales (SSO requirement)
- Reduces technical debt interest

Risk Assessment:

Current Vulnerabilities:
🚨 Security issues identified
   • Risk: Data breach, user account compromise
   • Severity: High
   • Likelihood: Medium (not exploited yet)
   • Cost if breached: $500k - $2M (estimate)

Technical Debt Cost:
💸 Ongoing maintenance: 10 hours/month
   • Legacy code, hard to change
   • Security patches require custom work
   • Hiring harder (outdated tech)
   • 120 hours/year = $12k/year waste

Effort Estimate:
⏱ 6-8 weeks (2-person team)
   • Research & design: 1 week
   • Implementation: 3 weeks
   • Migration planning: 1 week
   • Testing & rollout: 2 weeks
   • Buffer: 1 week

Cost: ~$60k (8 weeks @ $100/hr avg)

ROI Calculation:

Investment: $60k one-time
Returns:
+ Avoid security breach: $500k-2M (risk mitigation)
+ Reduce maintenance: $12k/year ongoing
+ Enable enterprise sales: $100k+/year potential
+ Faster feature development: 15% efficiency gain

Payback period: <1 year
ROI: 5-10x over 3 years

Recommendation: BUILD SOON (Q2-Q3)

Why build:
• Security vulnerabilities are real risk
• ROI is positive even without breach
• Unblocks future features (SSO)
• Maintenance burden increasing
• Industry standard (should have done earlier)

Why not "build immediately":
• Not actively being exploited (monitored)
• Can sequence after current sprint
• Need proper planning for migration
• User communication required

Sequencing Strategy:

Option A: Prioritize Security (Recommended)
Q2: OAuth migration (6-8 weeks)
Q3: Feature development resumes

Option B: Parallel Track
Q2: Features continue + spike OAuth (1-2 weeks)
Q3: OAuth migration (6-8 weeks)
Q4: Features accelerate (cleaner codebase)

Option C: Defer (Not Recommended)
Risk: Security incident, increasing tech debt
Only if: No vulnerabilities, compliance not needed

Mitigation Plan (while in backlog):
□ Monitor for exploitation attempts
□ Apply security patches as needed
□ Document migration plan
□ Allocate Q2 or Q3 slot
□ Communicate timeline to stakeholders

Success Metrics:
- Zero security incidents during/after migration
- 100% users migrated without issues
- <5% support ticket increase during rollout
- No performance regression
- 50% reduction in auth-related bugs
- SSO feature enabled for enterprise (follow-up)

Comparison to Feature Work:

If typical feature has RICE of 40:
OAuth migration "effective RICE": 60-80
(When accounting for risk mitigation + maintenance savings)

Think of it as:
- Reach: All users (security affects everyone)
- Impact: 2.0 (invisible but critical)
- Confidence: 90% (clear technical path)
- Effort: 8 weeks

"RICE": (5000 × 2.0 × 0.9) / 8 = 1,125 per week = 67.5

Recommendation: Treat as HIGH priority, sequence appropriately

Time to generate: 5 minutes
For implementation plan: Use /improvement-proposals skill
For cost details: Use /quick-cost-estimate command
```

## Estimation Methodology

The command uses RICE framework with rapid analysis:

### Reach Estimation

```
How many users affected per quarter?

Sources:
- Analytics: Active users per feature area
- Surveys: "Would you use this?"
- Support tickets: Request frequency
- Market data: Industry benchmarks

Typical ranges:
- All users: 100% of user base
- Power users: 20-40%
- Specific segment: 10-30%
- Niche feature: <10%
```

### Impact Scoring

```
How much does it help each user?

Scale:
3.0 = Massive  - Transforms workflow, can't live without
2.0 = High     - Major improvement, very helpful
1.0 = Medium   - Nice improvement, moderately helpful
0.5 = Low      - Small improvement, slightly helpful
0.25 = Minimal - Barely noticeable

Factors:
- Time saved per use
- Frequency of use
- Pain point severity
- Alternatives available
```

### Confidence Assessment

```
How sure are you about reach/impact?

100% = Proven (already tested/validated)
80%  = High (strong data, clear demand)
50%  = Medium (some data, reasonable assumptions)
20%  = Low (speculation, many unknowns)

Increase confidence by:
- User research/interviews
- Prototype testing
- Analytics validation
- Technical spikes
```

### Effort Estimation

```
How many person-weeks to build?

Includes:
- Design and planning
- Implementation
- Testing and QA
- Documentation
- Deployment

Common ranges:
- Small: 1-2 weeks
- Medium: 2-4 weeks
- Large: 4-8 weeks
- Major: 8-16 weeks
```

## Output Format

Every impact estimate includes:

1. **RICE Score & Priority**
   - Calculated score
   - Priority recommendation (Very High, High, Medium, Low)

2. **RICE Breakdown Table**
   - Each component explained
   - Reasoning for each score

3. **Impact Analysis**
   - User value
   - Business value
   - Risks and uncertainties

4. **Recommendation**
   - Clear go/no-go guidance
   - When to build
   - Success metrics

5. **Context Considerations**
   - Customer requests
   - Strategic value
   - Technical debt factors

## Limitations

**Quick estimate is NOT suitable for**:
- Detailed business cases
- Executive presentations
- Complex features with dependencies
- Strategic product direction
- Comprehensive PRDs

**Accuracy factors**:
- ±40% on RICE scores
- Best for relative prioritization
- Assumes reasonable estimates
- No detailed user research
- Quick directional guidance

## RICE Interpretation Guide

```
RICE Score Ranges:

80+   = VERY HIGH - Top priority candidates
40-79 = HIGH      - Strong candidates for roadmap
20-39 = MEDIUM    - Consider if capacity allows
10-19 = LOW       - Probably defer
<10   = VERY LOW  - Don't build

But also consider:
- Strategic value (enterprise deals, partnerships)
- Technical dependencies (blockers)
- Time sensitivity (market window)
- Customer commitments
```

## Common Use Cases

### Sprint Planning
```bash
/feature-impact-estimate [feature1]
/feature-impact-estimate [feature2]
# Compare RICE scores to prioritize
```

### Customer Requests
```bash
/feature-impact-estimate [requested feature] --context "Enterprise customer request"
# Evaluate if worth building
```

### Roadmap Planning
```bash
/feature-impact-estimate [Q2 candidate 1]
/feature-impact-estimate [Q2 candidate 2]
/feature-impact-estimate [Q2 candidate 3]
# Rank by RICE for quarterly plan
```

### Quick Sanity Check
```bash
/feature-impact-estimate [idea]
# Is this worth exploring further?
```

### Tech Debt Decisions
```bash
/feature-impact-estimate [refactoring work] --context "Tech debt"
# Compare to feature work
```

## Tips for Better Estimates

1. **Be realistic on reach**: Don't assume 100% unless truly universal

2. **Conservative on impact**: 3.0 is RARE (transformative features only)

3. **Honest about confidence**: Low confidence = need more research

4. **Include all effort**: Don't forget testing, docs, deployment

5. **Use context**: Share customer requests, strategic value, constraints

6. **Compare relatively**: RICE best for ranking, not absolute priority

7. **Validate assumptions**: Quick estimates should trigger research, not replace it

## Integration with Other Skills

- **improvement-proposals**: Use RICE to prioritize which PRDs to write
- **competitive-intelligence**: Understand market expectations (impacts reach/impact)
- **persona-definition**: Better estimate reach and impact per user segment
- **changelog-creation**: Measure impact of shipped features vs estimates

## Related Commands

- `/improvement-proposals` - Full PRD for high RICE features
- `/quick-cost-estimate` - Detailed cost breakdown for effort validation
- `/quick-competitive-scan` - Check if feature is table stakes or differentiator
- `/persona-quick-reference` - Understand who benefits (reach/impact)

---

**Remember**: RICE scores are tools for discussion, not rules. Context matters. High RICE + strategic value = build. High RICE + no resources = still can't build. Use judgment.
