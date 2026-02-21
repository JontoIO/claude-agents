---
name: production-readiness-analysis
description: Launch readiness decision framework. Use when the user asks "are we ready to go to production?", "should we launch?", "estimate the impact of launching", or needs a go/no-go decision. Coordinates all available agents to produce a traffic-light dashboard and explicit launch verdict.
---

# Production Readiness Analysis Skill

You are performing a production readiness analysis. Your goal is to produce a clear go/no-go verdict backed by a multi-domain assessment. The output must be actionable: if the verdict is No-Go, the user must know exactly what to fix and in what order.

## When to Trigger

Trigger this skill when the user says:
- "Are we ready to go to production?"
- "Should we launch?"
- "Is [product name] production-ready?"
- "Estimate the impact of launching"
- "Production go/no-go"

## 6-Step Framework

### STEP 1: Product Readiness Check

Delegate to `product-manager` (if available):

- Is the MVP feature set complete? Which user stories are still open?
- Is there a defined definition of done for this launch?
- Have user acceptance tests been run or planned?
- What is the launch scope — full public launch, beta, soft launch?
- What is the target user segment for launch?

If `product-manager` is unavailable, ask the user directly:
- "Which features are complete vs. still in progress?"
- "What does 'done' look like for this launch?"
- "Who is the intended first audience?"

---

### STEP 2: Financial Readiness Check

Delegate to `financial-advisor` (if available):

- What is the current monthly burn rate and runway remaining?
- Does the pricing model support the launch (is it defined and tested)?
- What is the revenue model at launch — paid, freemium, beta/free?
- What are the projected launch costs (marketing, infrastructure scaling, support)?
- What is the break-even point and when is it expected to be reached?

If `financial-advisor` is unavailable, ask the user:
- "Do you have pricing defined?"
- "What is your current runway in months?"
- "Have you budgeted for launch-related costs (marketing, infra, support)?"

---

### STEP 3: Tax/Compliance Readiness Check

Delegate to `tax-advisor` (if available):

- Is the legal entity structure in place for the launch jurisdiction(s)?
- Are VAT/sales tax obligations understood and set up?
- Is privacy policy and terms of service in place (GDPR, CCPA if applicable)?
- Are there any outstanding compliance filings or registrations?
- Is the payment processor properly configured for tax collection?

If `tax-advisor` is unavailable, ask the user:
- "Do you have a legal entity registered in your primary launch market?"
- "Is your privacy policy and terms of service live?"
- "Is VAT/sales tax collection set up if you're charging customers?"

---

### STEP 4: Technical Readiness Check

Delegate to `ai-specialist` (if available):

- What is the current test coverage percentage?
- Are there any known critical or high-severity bugs open?
- Has the system been load tested for expected launch traffic?
- Is monitoring and alerting configured (error tracking, uptime, latency)?
- Is the deployment pipeline automated and tested?
- Are secrets and API keys properly managed (not hardcoded)?

If `ai-specialist` is unavailable, ask the user:
- "Do you have automated tests? What's your coverage estimate?"
- "Are there any known critical bugs?"
- "Do you have error monitoring set up (Sentry, Datadog, etc.)?"
- "Can you deploy without manual steps?"

---

### STEP 5: Risk Assessment

Synthesize risks from all agent outputs. Score each risk:

**Risk Score = Probability × Impact**
- Probability: Low (1) / Medium (2) / High (3)
- Impact: Low (1) / Medium (2) / High (3)
- Score range: 1-9

**Classify by score**:
- 🔴 Critical (7-9): Launch blocker — must resolve before go-live
- 🟡 High (4-6): Condition — resolve within 30 days of launch or document accepted risk
- 🟢 Acceptable (1-3): Monitor — acceptable to launch with this risk

Build a risk matrix table with all identified risks.

---

### STEP 6: Go/No-Go Decision

Apply the weighted scorecard:

| Domain | Weight | Score (0-10) | Weighted Score |
|--------|--------|--------------|----------------|
| Product | 30% | [0-10] | [weight × score] |
| Financial | 25% | [0-10] | [weight × score] |
| Tax/Legal | 20% | [0-10] | [weight × score] |
| Technical | 25% | [0-10] | [weight × score] |
| **Total** | **100%** | — | **[sum]** |

**Verdict thresholds**:
- **GO** (≥7.5): Launch is recommended
- **GO with conditions** (6.0-7.4): Launch is possible; listed conditions must be met first
- **NO-GO** (< 6.0): Do not launch; critical items must be resolved

**Auto-veto**: If any single domain scores ≤ 3/10, the verdict is automatic NO-GO regardless of total score. State the vetoing domain and reason.

---

## Output Format

```markdown
# Production Readiness Analysis — [Product Name]
**Date**: [Current date]
**Prepared by**: CEO Agent (coordinating: [agents used])

---

## 🚦 Launch Dashboard

| Domain      | Status | Score | Key Blocker (if any) |
|-------------|--------|-------|----------------------|
| Product     | 🟢/🟡/🔴 | X/10 | [issue or "None"] |
| Financial   | 🟢/🟡/🔴 | X/10 | [issue or "None"] |
| Tax/Legal   | 🟢/🟡/🔴 | X/10 | [issue or "None"] |
| Technical   | 🟢/🟡/🔴 | X/10 | [issue or "None"] |
| **OVERALL** | 🟢/🟡/🔴 | **X.X/10** | |

---

## ✅ / ❌ Verdict: [GO / GO WITH CONDITIONS / NO-GO]

[2-3 sentence decision rationale. Be explicit.]

---

## Critical Blockers (must fix before launch)

1. [Blocker 1] — Domain: [domain] — Est. fix time: [X days]
2. [Blocker 2] — ...
*(If none: "No critical blockers identified.")*

---

## Launch Conditions (fix within 30 days of launch)

1. [Condition 1] — Domain: [domain]
2. [Condition 2] — ...
*(If none: "No conditions. Proceed.")*

---

## Risk Matrix

| Risk | Domain | Probability | Impact | Score | Classification |
|------|--------|-------------|--------|-------|----------------|
| [Risk] | [domain] | High/Med/Low | High/Med/Low | [1-9] | 🔴/🟡/🟢 |

---

## 30-Day Launch Checklist

### Week 1 (pre-launch)
- [ ] [Task 1]
- [ ] [Task 2]

### Week 2-3 (launch week)
- [ ] [Task 3]
- [ ] [Task 4]

### Week 4 (post-launch)
- [ ] [Task 5]
- [ ] [Task 6]

---

## Estimated Time to Production-Ready

[If NO-GO or GO WITH CONDITIONS: "Estimated X-Y weeks to resolve blockers and meet conditions."]
[If GO: "Ready to launch. Suggested go-live date: [date or 'within X days']."]

---

## Missing Agent Capabilities

[List any unavailable agents and what they would have assessed.]
```

---

## Quality Standards

1. Every domain must receive a numeric score — never leave it blank
2. Blockers must be specific and actionable — not "fix bugs" but "resolve open critical bugs in payment flow"
3. The 30-day checklist must be executable by the team without further clarification
4. Confidence level must be stated for any domain assessed without a companion agent

---

**Reminder**: The CEO is accountable for the launch verdict. Do not hedge — give a clear GO or NO-GO with explicit conditions.
