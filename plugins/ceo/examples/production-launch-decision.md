# Example: Production Launch Decision — TaskFlow SaaS

This example demonstrates the CEO agent orchestrating all four marketplace agents to produce a go/no-go decision and 30-day launch plan for a SaaS project management tool.

---

## Scenario

**Company**: TaskFlow (bootstrapped, 2-person founding team)
**Product**: SaaS project management tool for freelancers and small agencies
**Stage**: MVP complete, private beta with 40 users, planning public launch
**Question asked**: *"We've had 40 beta users for 6 weeks. Can we launch publicly? What are we missing?"*

---

## CEO Agent Response

*(Demonstrates the `production-readiness-analysis` skill)*

---

### Step 1: Agent Detection

```
Scanning for companion agents...
✅ financial-advisor found at ../financial-advisor/agents/financial-advisor.md
✅ product-manager found at ../product-manager/agents/product-manager.md
✅ tax-advisor found at ../tax-advisor/agents/tax-advisor.md
✅ ai-specialist found at ../ai-specialist/agents/ai-specialist.md

All 4 agents available. Proceeding with full orchestration.
```

---

### Step 2: Agent Delegation (parallel)

**CEO → product-manager**: "Assess MVP completeness for public launch. 40 beta users, 6 weeks. What product gaps exist? Is the user experience ready for general public?"

**CEO → financial-advisor**: "Assess financial readiness for public launch. What is the runway? Is pricing set? What will launch cost (marketing, infrastructure scaling)? Break-even point?"

**CEO → tax-advisor**: "Assess legal/compliance readiness for public launch. Is there a legal entity? Privacy policy? Terms of service? VAT obligations if EU customers? Stripe tax configuration?"

**CEO → ai-specialist**: "Assess technical readiness for public launch. Test coverage, open critical bugs, monitoring setup, deployment pipeline, security posture?"

---

### Step 3: Agent Outputs

---

#### Product Manager Assessment

**Feature completeness**: Core MVP is complete — task creation, project boards, time tracking, basic reporting. The following user stories from the beta feedback backlog are open:

- **P1**: Bulk task import (35% of beta users requested, blocking 3 enterprise prospects)
- **P1**: Email notifications (users missing deadlines without it)
- **P2**: Recurring tasks (nice-to-have, not launch-blocking)
- **P3**: API access (needed for enterprise, not MVP scope)

**Beta signal**: NPS from 40 beta users = 42 (good). Top pain: email notifications missing. 5 beta users converting to paid waitlist — validated willingness to pay.

**Launch scope recommendation**: Soft launch (100-500 targeted users, not broad marketing) is viable if email notifications are shipped. Full public launch recommended after 4 more weeks to address P1 items.

**User persona validation**: Primary persona confirmed as freelance designers and developers (15-50 person agencies). Secondary persona (solopreneurs) engaged less — deprioritize for launch messaging.

---

#### Financial Advisor Assessment

**Current financial position**:
- Runway: 11 months (bootstrapped, minimal burn)
- Current burn: $3,200/month (infra $200, tools $300, founder time opportunity cost estimated at $2,700)
- Revenue: $0 (beta is free)

**Pricing**: Not finalized. Comparable tools charge $12-25/user/month. Recommended: $15/user/month Starter (up to 5 users), $35/month Pro (unlimited users), $99/month Agency (multi-client).

**Launch cost estimate**:
- Infrastructure scaling (10x beta): +$400/month (AWS upgrade)
- Email service (SendGrid): +$20/month
- Customer support tool (Intercom): +$39/month
- Launch marketing (ProductHunt, Twitter ads): $500-2,000 one-time
- Total launch cost: ~$2,500 one-time, +$460/month ongoing

**Break-even**: 15 Pro subscribers or 30 Starter subscribers = break-even on operational costs. Full runway payback at 50 Pro subscribers.

**Financial risk**: LOW at current scale. Risk escalates if viral growth spikes infrastructure costs — recommend setting Claude API usage caps per user.

---

#### Tax Advisor Assessment

**Entity status**: Operating as sole trader (Spain). Adequate for current scale. If monthly revenue exceeds €3,000, recommend transitioning to SL (Sociedad Limitada) within 12 months for liability protection and tax optimization.

**Privacy policy**: NOT in place. Required before any public launch (GDPR applies immediately with EU users).

**Terms of service**: NOT in place. Required before accepting payments.

**VAT/IVA obligations**:
- Domestic (Spain): 21% IVA on B2C SaaS sales. Must register for IVA and file quarterly.
- EU cross-border B2C: OSS (One Stop Shop) registration required once EU sales begin — register before exceeding €10,000 threshold.
- B2B (reverse charge): No IVA obligation if selling to VAT-registered EU businesses.

**Stripe Tax**: Not configured. Must configure for correct IVA/VAT calculation and collection before first paid transaction.

**Critical compliance gap**: Privacy policy and ToS are launch blockers. Cannot legally collect user data or payments without them. Estimated 2-3 days to produce with a template-based approach.

---

#### AI Specialist Assessment

**Test coverage**: 31% (low). Payment flow has zero automated tests — critical gap.

**Critical bugs**: 3 open
- 🔴 BUG-47: Payment fails for non-EU Stripe customers (cannot accept payments from US users)
- 🔴 BUG-52: Session token not invalidated on logout (security vulnerability)
- 🟡 BUG-61: File upload fails >5MB (cosmetic for MVP, not launch-blocking)

**Monitoring**: No error tracking (no Sentry or equivalent). No uptime monitoring. Cannot detect production failures without manual user reports.

**Deployment pipeline**: Manual SSH deployment. No CI/CD. High risk of deployment errors during a high-traffic launch moment.

**Security**: API keys hardcoded in `.env` committed to private repo (acceptable but should move to secrets manager). Session management vulnerability (BUG-52) must be fixed before launch.

**Infrastructure**: Single EC2 t3.small. Will not handle >200 concurrent users. Upgrade needed before launch marketing begins.

---

### Step 4: Cross-Domain Synthesis

**Conflicts identified**:
- `⚡` Financial says "launch cost is manageable" — but Technical says infra will fail at launch traffic without upgrade (the upgrade cost is included in financial estimate, but sequencing matters: upgrade must happen before marketing spend)

**Alignments**:
- Product + Financial align: soft launch (100-500 users) is the right scope — affordable, achievable, enough signal
- Tax + Technical align: both have launch-blocking items (privacy policy, critical bugs) that must be resolved in parallel
- All 4 agents agree: full public launch is 3-4 weeks away, not today

**Dependencies**:
- BUG-52 (security) → must be fixed before any public-facing launch
- Privacy policy + ToS → must be live before Stripe payments enabled
- Stripe Tax configuration → blocks first paid transaction
- Infrastructure upgrade → must precede launch marketing

---

### Step 5: Production Readiness Dashboard

| Domain | Status | Score | Blocker |
|--------|--------|-------|---------|
| Product | 🟡 | 6.5/10 | Email notifications missing |
| Financial | 🟢 | 8.0/10 | None (pricing needs finalizing) |
| Tax/Legal | 🔴 | 3.5/10 | No privacy policy or ToS |
| Technical | 🔴 | 4.0/10 | 2 critical bugs, no monitoring |
| **OVERALL** | 🔴 | **5.5/10** | |

---

## ❌ Verdict: NO-GO

**Score 5.5/10** — below the 7.5 GO threshold.

Tax/Legal auto-veto (3.5/10): Cannot launch without a privacy policy and terms of service. This is a legal requirement, not a best practice. Any data collected from public users without a privacy policy creates immediate GDPR liability.

Technical domain is also below acceptable threshold (4.0/10): A session token vulnerability and a broken payment flow for US customers cannot be shipped to the public.

---

## Critical Blockers (must fix before launch)

1. **No Privacy Policy** (Tax/Legal) — GDPR violation risk. Fix: Use a GDPR-compliant template, customize for TaskFlow. Est. time: 2-3 days.
2. **No Terms of Service** (Tax/Legal) — Cannot accept payments legally. Fix: Use a template, customize. Est. time: 1-2 days.
3. **BUG-52: Session token not invalidated on logout** (Technical) — Security vulnerability. Fix: Backend session management update. Est. time: 1-2 days.
4. **BUG-47: Payment fails for non-EU customers** (Technical) — Cannot accept revenue from US market. Fix: Stripe configuration update. Est. time: 1-3 days.
5. **No error monitoring** (Technical) — Cannot detect production failures. Fix: Install Sentry (free tier adequate for launch). Est. time: 4 hours.

---

## Launch Conditions (address within 30 days of launch)

1. Ship email notifications (Product) — 35% of beta users blocked by this
2. Configure Stripe Tax for IVA/VAT collection (Tax)
3. Register for Spanish IVA quarterly filing (Tax)
4. Upgrade infrastructure to t3.medium + configure auto-scaling (Technical)
5. Set up CI/CD pipeline with GitHub Actions (Technical)
6. Finalize and test pricing tiers in Stripe (Financial)

---

## 30-Day Launch Checklist

### Week 1 — Resolve Blockers
- [ ] Draft Privacy Policy using GDPR template (Legal/Founder)
- [ ] Draft Terms of Service (Legal/Founder)
- [ ] Fix BUG-52: session token invalidation (Engineering)
- [ ] Fix BUG-47: non-EU payment failure (Engineering)
- [ ] Install Sentry for error tracking (Engineering, 4 hours)
- [ ] Upgrade EC2 to t3.medium (Engineering, 1 hour)

### Week 2 — Launch Conditions
- [ ] Ship email notifications feature (Engineering)
- [ ] Configure Stripe Tax for Spain IVA (Finance/Founder)
- [ ] Set up pricing tiers in Stripe (Finance/Founder)
- [ ] Implement CI/CD with GitHub Actions (Engineering)

### Week 3 — Soft Launch Preparation
- [ ] Import 10 invited users (from waiting list) — canary test
- [ ] Monitor Sentry for 48 hours post-import
- [ ] Register for IVA OSS if EU users are expected (Tax)
- [ ] Prepare ProductHunt launch assets (Marketing)
- [ ] Set up Intercom for customer support (Product)

### Week 4 — Soft Launch
- [ ] Open registration to 100 invited users
- [ ] Monitor: Sentry errors, Stripe conversions, user activation rate
- [ ] Capture first paying customer 🎉
- [ ] Schedule post-launch retrospective for Week 5

---

## Missing Agent Capabilities

All 4 agents were available. No capability gaps in this assessment.

---

## Estimated Time to Production-Ready

**3 weeks** to resolve all critical blockers and meet launch conditions.

**Recommended soft launch date**: [Current date + 21 days]
**Recommended full public launch**: [Current date + 35 days] (after soft launch validation)

---

*CEO Agent | coordinating: financial-advisor, product-manager, tax-advisor, ai-specialist*
