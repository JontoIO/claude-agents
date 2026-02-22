---
name: regression-testing
description: Run all active HP files against a live environment, record PASS/FAIL/SKIP for each step, produce a summary dashboard table, and auto-generate BUG-XXX reports for every failure. Designed to be run before releases or after significant changes to verify nothing has regressed.
---

# Regression Testing Skill

## When to Use

- Before any production release
- After merging a large PR or feature branch
- After a dependency update (especially framework or auth library upgrades)
- After a hotfix to verify the fix didn't break adjacent flows
- On a schedule (e.g., weekly) to catch silent regressions
- Any time someone asks: "run regression", "test all happy paths", "pre-release check"

---

## 4-Step Framework

### Step 1: HP File Inventory (5 min)

**Objective**: Load all active HP files and confirm scope with the user.

**Actions**:

1. Glob for HP files: `happy-path/HP-*.md` in the target project
2. Read each file's frontmatter to extract: `id`, `name`, `status`, `priority`
3. Filter to only `status: active` files (skip `draft` and `deprecated`)
4. Present inventory to user:

```
## Regression Scope

Found [N] active HP files:
| ID | Name | Priority | Tags |
|----|------|----------|------|
| HP-001 | User Login | P0 | auth |
| HP-002 | Checkout Flow | P0 | checkout, payment |
| HP-003 | Product Search | P1 | search |
...

**Base URL**: [ask user to confirm]
**Auth**: [ask if any HP steps require authentication — collect token/cookie if needed]
**Scope**: Run all [N] active HPs? Or filter by priority/tag?
```

5. Use `AskUserQuestion` to confirm:
   - Base URL
   - Whether to run all HPs or a filtered subset (by priority or tag)
   - Whether to auto-generate BUG reports for failures

**Output**: Confirmed list of HP files to execute, base URL, auth credentials if needed.

---

### Step 2: Execution

**Objective**: Execute each HP step and record results.

**Per HP file**:

1. **Check prerequisites**: Verify the app is reachable at base URL:
   ```bash
   curl -s -o /dev/null -w "%{http_code}" [base-url]
   ```
   If unreachable, mark all steps in this HP as SKIP and note the reason.

2. **Execute each step**:
   - For URL/page steps: `curl -s -w "\n%{http_code} %{time_total}s" [base-url][path]`
   - For API endpoint steps: construct the curl command from the step's Action field
   - For UI interaction steps that require a browser: mark as SKIP (cannot execute without browser) and note

3. **Record result for each step**:
   - ✅ **PASS**: HTTP status matches expected, response time < 3s, content matches expected
   - ❌ **FAIL**: Status mismatch, timeout, empty body when content expected, or error message in response
   - ⏭️ **SKIP**: Prerequisite not met, requires browser/auth not provided, or step is browser-only

4. **Note evidence** for every FAIL:
   - Full curl command used
   - Full response (status + body)
   - Which HP step failed

**Output**: Per-HP execution log with step-level PASS/FAIL/SKIP and evidence for failures.

---

### Step 3: Regression Report

**Objective**: Produce a clear, actionable summary of the regression run.

**Report Format**:

```markdown
# Regression Report — YYYY-MM-DD

**Environment**: [base-url]
**Scope**: [N] HP files, [N] steps
**Duration**: [X minutes]
**Overall Status**: 🟢 All pass / 🟡 Partial failures / 🔴 Critical failures

## Summary Dashboard

| HP | Name | Priority | Result | Pass | Fail | Skip |
|----|------|----------|--------|------|------|------|
| HP-001 | User Login | P0 | ✅ PASS | 5 | 0 | 0 |
| HP-002 | Checkout Flow | P0 | ❌ FAIL | 3 | 2 | 0 |
| HP-003 | Product Search | P1 | ✅ PASS | 4 | 0 | 1 |

**Totals**: [N] pass, [N] fail, [N] skip across [N] steps

## Failures Detail

### HP-002: Checkout Flow — Step 3: Payment Submission
**Expected**: POST /api/checkout returns 201 with order ID
**Actual**: POST /api/checkout returned 500

**Evidence**:
```
curl -X POST -H "Content-Type: application/json" \
  -d '{"cart_id":"test-123","payment_method":"card"}' \
  http://localhost:3000/api/checkout

HTTP/1.1 500 Internal Server Error
{"error":"Payment processor unavailable","code":"STRIPE_TIMEOUT"}
```

**BUG Report**: → BUG-001 generated (see below)

## Bug Reports Generated

[List of auto-generated BUG-XXX reports, pending user confirmation before persisting]
```

**Traffic Light Logic**:
- 🟢 All active P0 and P1 HPs pass
- 🟡 Any P1 HP has failures, or > 20% of steps fail overall
- 🔴 Any P0 HP has failures, or > 50% of steps fail overall

**Output**: Full regression report with dashboard and failure details.

---

### Step 4: Post-Regression Actions

**Objective**: Turn regression results into actionable next steps.

**Actions**:

1. **For each FAIL**: Auto-generate a BUG-XXX draft report using the bug-hunt template
   - Pre-fill: `found-date`, `severity` (based on HP priority), `component`, `steps-to-reproduce`, `evidence`
   - Ask user to confirm before writing to `happy-path/bugs/BUG-XXX.md`

2. **For steps that were SKIP due to changed behavior**: Offer to update the HP file
   - "Step 3 expected status 201 but consistently returns 200 — is this an intentional API change?"
   - If yes: offer to update the HP file's Expected field

3. **For uncovered areas**: Suggest new HP files for flows not currently tested
   - Compare discovered routes (from Glob) against existing HP coverage
   - List top 3 uncovered P0/P1 flows and ask if user wants to create HPs for them

4. **Release recommendation**:
   - 🟢 PASS: "All active HP flows pass. ✅ Green to release."
   - 🟡 WARN: "P1 failures present. 🟡 Recommend fixing [BUG-XXX] before release."
   - 🔴 BLOCK: "P0 failure: [HP-XXX] — [BUG-XXX]. 🔴 Do not release until resolved."

**Output**: BUG-XXX reports (pending confirmation), HP update proposals, release recommendation.

---

## Execution Notes

### Authentication Handling
If HP steps require authentication:
1. Ask user for a test auth token or session cookie before running
2. Inject via: `curl -H "Authorization: Bearer [token]"` or `-H "Cookie: session=[value]"`
3. Flag any HP step that requires auth but no credentials were provided as SKIP

### Browser-Only Steps
Steps that require JavaScript execution (clicking buttons, filling forms in a SPA) cannot be run via curl:
- Mark as SKIP
- Note: "Cannot execute browser interaction via curl — manual verification required"
- These steps should be manually verified before marking the HP as fully passing

### Parallel Execution
For large regression suites (10+ HPs), group by domain and run each domain's curls in sequence to avoid overwhelming the server. Do NOT run all endpoints simultaneously.

### Flaky Tests
If a step fails once but passes on retry:
- Note as "Intermittent" in the report
- Still generate a BUG-XXX with severity one level lower than the HP priority
- Add to "Common Failure Patterns" in the HP file

---

## Tips

- Run regression on a staging environment, not production, to avoid affecting real users
- Keep a regression history by naming reports `regression-YYYY-MM-DD.md` in `happy-path/reports/`
- The first regression run on a new codebase will have many SKIPs — that's expected; it surfaces gaps
- Compare consecutive regression reports to detect trends (new failures, fixed bugs, new SKIPs)

## Common Mistakes to Avoid

- Do NOT mark a step as PASS if you only checked the HTTP status — also verify response content
- Do NOT skip the user confirmation on BUG-XXX creation — even if it's automated, the user needs to know
- Do NOT run regression against production without explicit user confirmation
- Do NOT treat SKIP as PASS — SKIPs represent untested coverage that should be addressed
