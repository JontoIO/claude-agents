# Example: E-Commerce Checkout QA

This example demonstrates the qa-engineer plugin in action on a fictional e-commerce platform. It walks through all three core skills: happy-path-mapping, bug-hunt, and regression-testing.

## Project Context

**Application**: ShopFast — a Next.js e-commerce platform with a Stripe-powered checkout.
**Stack**: Next.js 14, PostgreSQL, Stripe, Redis (session), Vercel deployment.
**Base URL**: `http://localhost:3000` (development)

---

## Scenario 1: Initial QA Baseline (Happy Path Mapping)

### User Prompt
> "We've never done formal QA. Map all our happy paths."

### QA Engineer Response

**Step 1: Flow Discovery**

```
Globbing routing files...
Found: pages/index.js, pages/products/[slug].js, pages/cart.js,
       pages/checkout.js, pages/checkout/success.js,
       pages/api/auth/[...nextauth].js, pages/api/cart/index.js,
       pages/api/orders/index.js, pages/api/orders/[id].js,
       pages/api/checkout/index.js, pages/account/orders.js,
       pages/admin/products.js, pages/admin/orders.js
```

**Step 2: Prioritized Flow List**

| Priority | Flow | Route | Reason |
|----------|------|-------|--------|
| P0 | User Login | /api/auth | Auth gate for all protected flows |
| P0 | Checkout & Payment | /checkout → /api/checkout | Revenue-critical |
| P0 | Cart Management | /cart, /api/cart | Prerequisite for checkout |
| P1 | Product Browse | /products/[slug] | Core product experience |
| P1 | Order History | /account/orders | Post-purchase trust |
| P2 | Guest Checkout | /checkout (no auth) | Alternative purchase path |
| P3 | Admin: Product CRUD | /admin/products | Internal tool |

**Step 3: AskUserQuestion — Confirmation**

```
I've discovered 7 significant flows. I'd like to create the following HP files:
- HP-001: User Login (P0)
- HP-002: Add to Cart (P0)
- HP-003: Checkout & Payment (P0)
- HP-004: Product Browse & Detail (P1)
- HP-005: Order History (P1)
- HP-006: Guest Checkout (P2)
- HP-007: Admin Product Management (P3)

Create all 7 as draft HP files in happy-path/?
```

User confirms → 7 files created.

---

### Generated HP File Example: HP-003

**File**: `happy-path/HP-003.md`

```markdown
---
id: HP-003
name: Checkout & Payment
status: draft
created: 2026-02-22
updated: 2026-02-22
author: qa-engineer
priority: P0
tags: [checkout, payment, stripe, order]
---

# HP-003: Checkout & Payment

## Overview
Validates the complete purchase flow from cart review through Stripe payment processing to order confirmation. This is the most revenue-critical flow in the application.

## Prerequisites
- [ ] Application is running at http://localhost:3000
- [ ] Logged-in user account with verified email
- [ ] At least 1 item in cart
- [ ] Stripe test mode enabled (key: sk_test_...)
- [ ] Database is seeded with at least 1 product in stock

## Test Steps

### Step 1: Navigate to Checkout
**Action**: GET http://localhost:3000/checkout
**Expected**: HTTP 200, page renders with cart items listed and total price
**Actual**: [ ] Pass / [ ] Fail — [notes]

### Step 2: Enter Shipping Details
**Action**: Fill form — name, address, city, postal code, country
**Expected**: Form validates inline; "Continue to Payment" button becomes active
**Actual**: [ ] Pass / [ ] Fail — [notes]

### Step 3: Enter Payment Details
**Action**: Fill Stripe test card: 4242 4242 4242 4242, exp 12/34, CVV 123
**Expected**: Stripe.js loads, card field renders, no console errors
**Actual**: [ ] Pass / [ ] Fail — [notes]

### Step 4: Submit Payment
**Action**: Click "Place Order" → POST /api/checkout
**Expected**: HTTP 201, response body includes `{ order_id: "...", status: "confirmed" }`
**Actual**: [ ] Pass / [ ] Fail — [notes]

### Step 5: Verify Confirmation Page
**Action**: Browser redirects to /checkout/success?order_id=[id]
**Expected**: HTTP 200, order ID displayed, confirmation email triggered
**Actual**: [ ] Pass / [ ] Fail — [notes]

## Success Criteria
- [ ] Order created in database with status "confirmed"
- [ ] Stripe payment intent shows as "succeeded" in Stripe dashboard
- [ ] Confirmation email sent to user
- [ ] No console errors during entire flow
- [ ] All HTTP responses complete within 3 seconds

## Common Failure Patterns
- **Stripe timeout**: Payment intent creation exceeds 10s — check Stripe status page
- **CSRF mismatch**: Session cookie expired mid-flow — ensure session TTL > checkout duration
- **Stock race condition**: Item sold out between cart add and checkout — check inventory lock

## Related Flows
- [HP-002: Add to Cart] — Must complete before checkout
- [HP-005: Order History] — Checkout creates orders visible here
- [HP-006: Guest Checkout] — Same flow without authentication

## Notes
Use Stripe test card 4000 0027 6000 3184 to test EU 3DS authentication flow.
Production has a 15-minute checkout session timeout — test does not enforce this.
```

---

## Scenario 2: Pre-Release Bug Hunt

### User Prompt
> "We're deploying tomorrow. Run a bug hunt."

### QA Engineer Response

**Base URL confirmed**: `http://localhost:3000`

**Category 1: Console Error Patterns**

```bash
# Grep results:
src/lib/stripe.js:34 — JSON.parse without try/catch
src/pages/api/orders/[id].js:67 — .then() without .catch()
src/components/CartItem.js:23 — props.product.price.toFixed() (no null check)
```

**Category 2: Broken Pages**

```bash
curl -s -o /dev/null -w "%{http_code} %{time_total}s" http://localhost:3000/
# → 200 0.245s ✅

curl -s -o /dev/null -w "%{http_code} %{time_total}s" http://localhost:3000/checkout
# → 200 0.312s ✅

curl -s -o /dev/null -w "%{http_code} %{time_total}s" http://localhost:3000/account/orders
# → 500 0.089s ❌ CRITICAL
```

**Category 3: Broken Endpoints**

```bash
curl -s -w "\n%{http_code}" http://localhost:3000/api/health
# → {"status":"ok","db":"connected"}\n200 ✅

curl -X POST -H "Content-Type: application/json" \
  -d '{"productId":"test-1","quantity":1}' \
  http://localhost:3000/api/cart
# → 201 ✅

curl -s http://localhost:3000/api/orders
# → 401 ✅ (correctly requires auth)

curl -s http://localhost:3000/api/admin/products
# → 200 ⚠️ SECURITY: Returns data without auth check!
```

**Category 4: UX Issues**

```bash
curl -s http://localhost:3000/ | grep -i "viewport"
# → <meta name="viewport" content="width=device-width, initial-scale=1"> ✅

curl -L -w "\n%{url_effective}" http://localhost:3000/login
# → http://localhost:3000/auth/signin ✅ (expected redirect)
```

### Bug Reports Generated

**BUG-001 (P0) — /account/orders returns 500**

```markdown
---
bug-id: BUG-001
severity: P0
status: open
found-by: qa-engineer
found-date: 2026-02-22
component: Account / Order History
---

# BUG-001: /account/orders returns 500 Internal Server Error

## Severity
**P0** — Critical: Logged-in users cannot view their order history.

## Steps to Reproduce
1. Navigate to http://localhost:3000/account/orders

## Expected vs Actual
**Expected**: HTTP 200, order history page renders
**Actual**: HTTP 500, page crashes

## Evidence
```
curl -s -w "\n%{http_code}" http://localhost:3000/account/orders
{"statusCode":500,"message":"Cannot read properties of undefined (reading 'id')"}
500
```

## Impact
- **Who**: All logged-in users
- **Frequency**: Every time
- **Business**: Post-purchase trust broken; users cannot verify orders

## Suggested Fix Direction
The error message "Cannot read properties of undefined (reading 'id')" suggests
a null reference in the orders query — likely `session.user.id` is undefined
when the page's getServerSideProps runs. Check session shape after NextAuth update.

## Related HP Files
- HP-005: Order History
```

**BUG-002 (P0) — Admin endpoint publicly accessible**

```markdown
---
bug-id: BUG-002
severity: P0
status: open
found-by: qa-engineer
found-date: 2026-02-22
component: API / Admin
---

# BUG-002: /api/admin/products returns data without authentication

## Severity
**P0** — Critical security issue: Admin product data exposed to unauthenticated users.

## Steps to Reproduce
1. curl http://localhost:3000/api/admin/products (no auth header)

## Expected vs Actual
**Expected**: HTTP 401 Unauthorized
**Actual**: HTTP 200 with full product catalog including cost prices

## Evidence
```
curl -s http://localhost:3000/api/admin/products
{"products":[{"id":"1","name":"Widget","price":29.99,"cost":4.50},...]}
```

## Impact
- **Who**: Anyone with network access
- **Frequency**: Every time
- **Business**: Cost price data exposed; competitor intelligence risk

## Suggested Fix Direction
Add authentication middleware to all /api/admin/* routes.
Check if NextAuth session guard is missing from this route handler.

## Related HP Files
- HP-007: Admin Product Management
```

**BUG-003 (P2) — Unsafe JSON.parse in stripe.js**

*(P2 because it's in error handling path, not happy path)*

---

### Bug Hunt Summary

```
## Bug Hunt Results

Scanned: 12 pages, 8 endpoints, 47 code files, 0 active HP files (drafts only)
Issues Found: 4 total — P0: 2 🔴, P1: 0, P2: 1 🟡, P3: 1 🟢

| Category | Checked | Issues | Severity |
|----------|---------|--------|----------|
| Console Errors | 47 files | 3 | P2: 1, P3: 2 |
| Broken Pages | 7 routes | 1 | P0: 1 |
| Broken Endpoints | 8 endpoints | 1 | P0: 1 (security) |
| UX Behavior | 2 flows | 0 | — |

🔴 DO NOT DEPLOY until BUG-001 and BUG-002 are resolved.
```

---

## Scenario 3: Post-Fix Regression Test

### User Prompt
> "We fixed BUG-001 and BUG-002. Run regression."

### QA Engineer Response

After activating 3 HP files (HP-001, HP-002, HP-003), regression is run:

```
## Regression Report — 2026-02-22

Environment: http://localhost:3000
Scope: 3 active HP files, 14 steps
Duration: 4 minutes

Overall Status: 🟢 PASS

| HP | Name | Priority | Result | Pass | Fail | Skip |
|----|------|----------|--------|------|------|------|
| HP-001 | User Login | P0 | ✅ PASS | 4 | 0 | 0 |
| HP-002 | Add to Cart | P0 | ✅ PASS | 3 | 0 | 1* |
| HP-003 | Checkout & Payment | P0 | ✅ PASS | 5 | 0 | 0 |

*HP-002 Step 4 (click "View Cart" button): SKIP — requires browser

Bug Reports Generated: None

Release Recommendation: ✅ Green to release. All active P0 HPs pass.

Suggested next step: Activate HP-005 (Order History) and re-run to confirm BUG-001 fix.
```

---

## Key Takeaways

1. **Happy path mapping** revealed 7 flows in 15 minutes, creating a QA baseline that didn't exist before.
2. **Bug hunt** caught a P0 security vulnerability (unauthenticated admin endpoint) before deployment.
3. **Regression testing** gave a clear go/no-go signal after the fix, with evidence for every decision.
4. **HP files** now live in `happy-path/` under version control — future developers can run regression at any time.
