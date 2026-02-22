# Quick Health Check Command

5-minute traffic-light snapshot of application health. Checks reachability, critical pages, health endpoints, and console error patterns — without modifying any files.

## Purpose

Use this command when:
- Starting a work session to verify the dev environment is up
- After a deployment to confirm the app is alive
- When a teammate says "the app seems slow or broken"
- Before starting a full regression run
- As a morning standup health check

## Command Format

```bash
/qa-engineer:quick-health-check [base-url]
```

### Optional Flags

```bash
--scope api          # Only check API endpoints (skip page checks)
--scope pages        # Only check HTML pages (skip API checks)
--scope all          # Default: check everything
--timeout 5000       # Request timeout in ms (default: 3000)
```

## Examples

### Basic Health Check
```bash
/qa-engineer:quick-health-check http://localhost:3000
```

### API-Only Check
```bash
/qa-engineer:quick-health-check http://localhost:3000 --scope api
```

### Staging Environment
```bash
/qa-engineer:quick-health-check https://staging.myapp.com
```

---

## Execution Steps

The command runs 5 checks in sequence, completing in under 5 minutes:

### Check 1: App Reachability (30 sec)
```bash
curl -s -o /dev/null -w "%{http_code} %{time_total}s" [base-url]
```
- 🟢 200 in < 1s
- 🟡 200 in 1-3s (slow)
- 🔴 Non-200, timeout, or connection refused

### Check 2: Critical Pages (2 min)
Curl the most important pages discovered in routing files (or default to `/`, `/login`, `/dashboard`, `/404`):
```bash
curl -s -o /dev/null -w "%{http_code} %{time_total}s" [base-url]/login
curl -s -o /dev/null -w "%{http_code} %{time_total}s" [base-url]/dashboard
```
- 🟢 All return 200 in < 3s
- 🟡 Any return 200 but slow (> 3s), or some return redirect chains
- 🔴 Any return 4xx or 5xx

### Check 3: Health Endpoints (1 min)
Check common health endpoint paths:
```bash
curl -s [base-url]/health
curl -s [base-url]/api/health
curl -s [base-url]/healthz
curl -s [base-url]/_health
curl -s [base-url]/status
```
Report which one responds and what it returns. If none found: 🟡 Warning (no health endpoint configured).

### Check 4: Console Error Patterns (1 min)
Quick grep of source files for highest-risk patterns:
```
Grep: \.catch\(\s*\)          → empty catch blocks
Grep: JSON\.parse(?!.*try)    → unsafe JSON parsing
Grep: console\.error\(        → known error conditions
```
- 🟢 0 matches
- 🟡 1-3 matches (low risk)
- 🔴 4+ matches or match in auth/payment code

### Check 5: Traffic-Light Summary (30 sec)
Compile all results into a single status dashboard.

---

## Output Format

```
## Quick Health Check — [base-url]
Completed in [X]s | [YYYY-MM-DD HH:MM]

| Check | Status | Detail |
|-------|--------|--------|
| App Reachability | 🟢 | 200 in 0.3s |
| Critical Pages | 🟡 | /dashboard: 504 |
| Health Endpoint | 🟢 | /api/health → {"status":"ok"} |
| Console Errors | 🟡 | 2 empty catch blocks found |

**Overall: 🟡 DEGRADED**

### Issues Found
- /dashboard returned 504 — possible backend timeout
- 2 empty catch blocks in src/api/orders.js:45 and src/utils/parser.js:12

### Recommended Next Steps
- [ ] Investigate /dashboard 504 — run `/qa-engineer:bug-hunt` on broken pages category
- [ ] Review empty catch blocks — may silently swallow errors in production
```

---

## Traffic Light Criteria

| Overall Status | Condition |
|----------------|-----------|
| 🟢 **HEALTHY** | All 5 checks green |
| 🟡 **DEGRADED** | Any check yellow, no checks red |
| 🔴 **CRITICAL** | Any check red |

---

## Limitations

- Does not execute JavaScript — SPA content rendering is not verified
- Cannot check authenticated routes without credentials (add `--auth-token` if needed)
- Console error detection is static analysis — may have false positives or miss runtime errors
- 5-minute target assumes < 20 routes; large apps may take longer

## When to Escalate

If the health check shows 🔴 CRITICAL:
1. Run full bug-hunt: "Run bug-hunt on this project"
2. Check deployment logs
3. Check database connectivity if pages are timing out
4. Escalate to on-call if this is a production environment
