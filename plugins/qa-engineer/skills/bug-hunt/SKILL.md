---
name: bug-hunt
description: Systematic 4-category bug detection covering JavaScript console errors (static analysis), broken pages (HTTP status checks), broken API endpoints (curl validation), and unexpected UX behavior (HP cross-reference). Produces structured BUG-XXX reports for every confirmed issue.
---

# Bug Hunt Skill

## When to Use

- After deploying a new feature or dependency update
- When a user reports "something feels off" without specifics
- Before a release as a pre-flight sanity check
- After restoring from a backup or migrating environments
- When a happy path step is failing and you need to isolate the cause
- Any time someone asks: "find bugs", "check for errors", "audit our endpoints", "what's broken"

---

## Bug Report Template

Every confirmed bug produces a BUG-XXX file (written to `happy-path/bugs/` in the target project, with user confirmation):

```markdown
---
bug-id: BUG-XXX
severity: P0 | P1 | P2 | P3
status: open
found-by: qa-engineer
found-date: YYYY-MM-DD
component: [Authentication, Checkout, API/orders, etc.]
---

# BUG-XXX: [Short descriptive title]

## Severity
**P0** — Critical (service down / data loss / checkout broken)
**P1** — High (core feature broken, workaround required)
**P2** — Medium (degraded experience, workaround exists)
**P3** — Low (cosmetic, minor)

## Steps to Reproduce
1. ...

## Expected vs Actual
**Expected**: ...
**Actual**: ...

## Evidence
```
[curl command + response pasted verbatim]
[grep output pasted verbatim]
```

## Impact
- **Who**: [All users / Logged-in / Admin only]
- **Frequency**: [Every time / Intermittent]
- **Business**: [Blocks checkout / Prevents login]

## Suggested Fix Direction
[QA's initial hypothesis — not a guaranteed root cause]

## Related HP Files
- [HP-XXX]
```

---

## 4-Category Detection Framework

### Category 1: Console Errors (Static Analysis)

**Objective**: Find code patterns that commonly produce runtime console errors.

**Actions**:

1. **Unhandled promise rejections**:
   ```
   Grep: \.catch\(\s*\)  (empty catch)
   Grep: async.*\{(?!.*try)  (async without try/catch)
   Grep: \.then\(.*\)(?!\.catch)  (then without catch)
   ```

2. **Missing null checks** (common crash sources):
   ```
   Grep: \.[a-z]+\.[a-z]+\.[a-z]+  (3+ deep property access without optional chaining)
   Grep: props\.[a-z]+ (React props without defaultProps or ?.)
   Grep: response\.data\.[a-z]+  (API response access without null guard)
   ```

3. **Unsafe JSON parsing**:
   ```
   Grep: JSON\.parse\(  — then check if surrounded by try/catch
   Grep: JSON\.parse(?!.*try)  (JSON.parse outside try block)
   ```

4. **Missing ErrorBoundary** (React projects):
   ```
   Grep: class.*extends.*Component  — verify at least one ErrorBoundary exists
   Grep: ErrorBoundary  — if 0 results, flag as missing
   ```

5. **Console.error calls** (may indicate known issues):
   ```
   Grep: console\.error\(
   Grep: console\.warn\(
   ```

**Severity Assignment**:
- Empty catch blocks on payment/auth flows → P0
- Missing null checks on API responses → P1
- Unsafe JSON.parse on user input → P1
- Missing ErrorBoundary on root component → P1
- Console.error in production code → P2

**Output**: List of code locations with pattern matches and severity assessment.

---

### Category 2: Broken Pages (HTTP Status Checks)

**Objective**: Verify every discovered route returns a valid HTTP response.

**Actions**:

1. Discover all page routes (from routing files — same glob patterns as happy-path-mapping Step 1)
2. For each route, run:
   ```bash
   curl -s -o /dev/null -w "%{http_code} %{time_total}s" [base-url][route]
   ```
3. Classify responses:
   - `200` + non-empty body → ✅ Pass
   - `200` + empty body → 🟡 Warning (possible render failure)
   - `301/302` → verify redirect target also returns 200
   - `404` → 🔴 Broken (route registered but not found)
   - `500/502/503` → 🔴 Critical
   - Response time > 3s → 🟡 Warning

4. For pages returning 200, verify non-empty content:
   ```bash
   curl -s [base-url][route] | wc -c  # must be > 500 bytes for a real page
   ```

5. Use WebFetch to check rendered page content for error messages:
   - "Something went wrong"
   - "Internal Server Error"
   - "Page not found" in body (not header)
   - Empty `<main>` or `<body>` tags

**Severity Assignment**:
- 500 on any page → P0 if auth/checkout, P1 otherwise
- 404 on a registered route → P1
- Empty 200 response → P2
- Response time > 3s → P2
- 404 on a deprecated/unregistered route → P3

**Output**: Table of all routes checked with status codes and response times.

---

### Category 3: Broken Endpoints (API Validation)

**Objective**: Verify API endpoints respond correctly to minimal valid requests.

**Actions**:

1. Discover API routes:
   - Glob: `**/api/**/*.{js,ts}`, `**/routes/**/*.{js,ts}`
   - Grep: `app\.(get|post|put|patch|delete)\(`, `@(Get|Post|Put|Patch|Delete)\(`
   - Check `openapi.yaml` or `swagger.json` if present

2. For each endpoint, construct a minimal valid request:
   - GET endpoints: `curl -s -w "\n%{http_code}" [base-url][path]`
   - POST endpoints (with Content-Type): `curl -s -w "\n%{http_code}" -X POST -H "Content-Type: application/json" -d '{}' [base-url][path]`

3. Validate response against 4 criteria:
   - **HTTP status**: Expected (200/201/204) vs actual
   - **Response time**: Must be < 3000ms (`%{time_total}` from curl)
   - **Valid JSON**: `curl ... | python3 -m json.tool` — must not error
   - **Required fields**: Check for `id`, `status`, `data`, `error` as appropriate

4. Check for authentication-required endpoints returning 200 without auth (security issue):
   ```bash
   curl -s -o /dev/null -w "%{http_code}" [base-url]/api/admin/users
   # Should return 401/403, not 200
   ```

5. Check CORS headers on API endpoints:
   ```bash
   curl -s -I -X OPTIONS [base-url]/api/[endpoint] | grep -i "access-control"
   ```

**Severity Assignment**:
- Auth-required endpoint returns 200 without credentials → P0 (security)
- Payment/order endpoint returns 500 → P0
- Core CRUD endpoint returns 500 → P1
- Invalid JSON response from any endpoint → P1
- Response time > 3s → P2
- Missing CORS headers on public API → P2
- Non-critical endpoint 404 → P3

**Output**: Table of all endpoints checked with status, response time, JSON validity, and auth behavior.

---

### Category 4: Unexpected UX Behavior

**Objective**: Identify UX issues that break expected user flows without necessarily causing HTTP errors.

**Actions**:

1. **Cross-reference HP files**: Read all active HP files from `happy-path/`, then for each step:
   - Check if the expected redirect actually happens
   - Check if success/error messages appear

2. **Broken redirects**:
   ```bash
   curl -s -L -w "\n%{url_effective} %{http_code}" [base-url]/login
   # Verify redirect chain ends at expected URL
   ```

3. **Form validation gaps**:
   - Grep for `required` attributes on form fields
   - Check if corresponding server-side validation exists (grep for `validate`, `schema`, `Joi`, `zod`, `yup`)
   - Flag forms with frontend-only validation and no backend guard

4. **Missing viewport meta** (mobile breakage):
   ```bash
   curl -s [base-url] | grep -i "viewport"
   # Must contain: <meta name="viewport" content="width=device-width, initial-scale=1">
   ```

5. **Broken asset URLs**:
   - Grep for hardcoded asset paths: `/public/`, `/static/`, `/assets/`
   - Curl each discovered asset URL to verify 200 response
   - Check for absolute URLs pointing to non-existent domains

6. **Accessibility quick-check**:
   - Grep for `alt=` on `<img` tags (missing alt = P3)
   - Grep for `aria-label` on interactive elements
   - Check `<title>` tag exists in HTML pages

**Severity Assignment**:
- Login redirect loop → P0
- Form submits silently with no feedback → P1
- Missing viewport meta → P2 (mobile users affected)
- Broken static asset (image/CSS/JS 404) → P2 if affects layout, P3 if cosmetic
- Missing alt text on images → P3

**Output**: List of UX issues with affected flows and HP file cross-references.

---

## Bug Hunt Summary Format

After running all 4 categories, produce:

```
## Bug Hunt Results

**Scanned**: [N] pages, [N] endpoints, [N] code files, [N] HP flows
**Issues Found**: [N] total — P0: N 🔴, P1: N 🟡, P2: N 🟡, P3: N 🟢

### Category Results
| Category | Checked | Issues | Severity |
|----------|---------|--------|----------|
| Console Errors | N files | N | P1: 2, P3: 1 |
| Broken Pages | N routes | N | P0: 1 |
| Broken Endpoints | N endpoints | N | P1: 3 |
| UX Behavior | N flows | N | P2: 2 |

### Critical Issues (P0/P1)
[List each with BUG-ID, title, severity, component]

### Bug Reports Generated
[List of BUG-XXX files created, pending user confirmation]
```

---

## Tips

- Always ask the user for `base-url` before running any curl commands
- If endpoints require authentication, ask for a test token or cookie before testing protected routes
- Focus on P0/P1 first — complete those before moving to P2/P3
- If the project has an existing test suite, grep for failing tests before manual curl testing — they may already document known issues
- For SPAs (React, Vue, Angular): page content checks via curl will only see the initial HTML shell, not rendered content — note this limitation explicitly

## Common Mistakes to Avoid

- Do NOT report a "bug" based solely on a grep match — always attempt to reproduce before filing BUG-XXX
- Do NOT curl authenticated endpoints and call them "broken" when they correctly return 401
- Do NOT create BUG-XXX files without user confirmation
- Do NOT conflate slow response (P2) with broken endpoint (P1) — both matter but differently
