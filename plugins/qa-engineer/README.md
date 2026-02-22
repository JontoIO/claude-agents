# QA Engineer Plugin

A methodical, evidence-based QA specialist for Claude that discovers happy paths, hunts bugs, and runs regression tests — producing structured HP-XXX and BUG-XXX artifacts that live alongside your code.

## Overview

The QA Engineer plugin brings systematic quality assurance to any codebase. Unlike generic testing advice, it actively inspects your project files, curls your endpoints, and produces structured living documentation (HP files) and actionable bug reports (BUG files) that your team can version-control and act on immediately.

**When to use this plugin**:
- You need to establish a QA baseline on a project that has no formal testing
- Before a major release to verify nothing is broken
- After a bug fix to create a regression test preventing recurrence
- When a stakeholder says "the app seems broken" and you need evidence
- On a schedule to catch silent regressions before users do

## Capabilities

### 1. Happy Path Mapping
Discover all significant user flows by scanning routing files, HTTP endpoints, form submissions, and navigation patterns. Generate numbered HP-XXX files using a consistent YAML-frontmatter template. Files are created in a `happy-path/` folder **in your target project** (not the plugin), where they belong under version control alongside the code they test.

HP files are living documents — they start as `draft`, become `active` after human review, and can be marked `deprecated` when flows are removed.

### 2. Happy Path Suggestion
Proactively surface new HP candidates from: recent git commits, incoming bug reports, coverage gaps vs. discovered routes, and related flows not yet documented. The agent always presents the full list and asks for confirmation before writing any file.

### 3. Bug Detection — 4 Categories

| Category | What's Checked |
|----------|---------------|
| **Console Errors** | Empty catch blocks, missing null checks, unsafe JSON.parse, missing ErrorBoundary |
| **Broken Pages** | HTTP status codes for all routes — flag 4xx/5xx, verify 200s have non-empty content |
| **Broken Endpoints** | curl API routes with minimal valid requests — check status, response time (<3s), valid JSON |
| **Unexpected UX** | Broken redirects, missing form validation, viewport meta, broken asset URLs, HP cross-reference |

### 4. Regression Testing
Load all `active` HP files, execute each step via curl/WebFetch, record PASS/FAIL/SKIP with evidence, produce a summary dashboard, and auto-generate BUG-XXX reports for every failure. Ends with a clear 🟢/🟡/🔴 release recommendation.

### 5. Environment Health Check
5-minute snapshot command that checks reachability, critical pages, health endpoints, and console error patterns — no file modifications, just a traffic-light status report.

## Available Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| [`happy-path-mapping`](./skills/happy-path-mapping/SKILL.md) | "map happy paths", "QA baseline", "what flows do we have" | Discover and document all user flows as HP-XXX files |
| [`bug-hunt`](./skills/bug-hunt/SKILL.md) | "find bugs", "check for errors", "audit endpoints" | 4-category systematic bug detection with BUG-XXX reports |
| [`regression-testing`](./skills/regression-testing/SKILL.md) | "run regression", "pre-release check", "test all HPs" | Execute all active HP files and produce pass/fail dashboard |

## Available Commands

| Command | Description |
|---------|-------------|
| [`/qa-engineer:quick-health-check [base-url]`](./commands/quick-health-check.md) | 5-minute traffic-light snapshot |
| [`/qa-engineer:suggest-happy-paths [scope]`](./commands/suggest-happy-paths.md) | Propose new HP files from code analysis |

## Usage Walkthrough

### Starting From Scratch

```
You: Map all the happy paths in this project.

QA Engineer: [Globs routing files, discovers 8 flows]

I found 8 flows. I'd like to create these HP files in happy-path/:
- HP-001: User Login (P0)
- HP-002: Checkout (P0)
- HP-003: Product Browse (P1)
...

Shall I create all 8 as draft HP files?

You: Yes, create all of them.

QA Engineer: [Writes HP-001 through HP-008, creates INDEX.md]

Created 8 HP files in happy-path/. All are status: draft — review
the test steps and mark them active when they look correct.
```

### Pre-Release Bug Hunt

```
You: /qa-engineer:quick-health-check http://localhost:3000

QA Engineer:
| Check | Status | Detail |
|-------|--------|--------|
| App Reachability | 🟢 | 200 in 0.3s |
| Critical Pages | 🔴 | /account/orders: 500 |
| Health Endpoint | 🟢 | {"status":"ok"} |
| Console Errors | 🟡 | 2 empty catch blocks |

Overall: 🔴 CRITICAL — found 1 broken page, BUG-001 generated.
```

### Regression After a Fix

```
You: We fixed the order history bug. Run regression on the checkout flows.

QA Engineer: [Runs HP-001, HP-002, HP-003 — all active P0 HPs]

Regression Report — 2026-02-22
All 3 P0 HPs: ✅ PASS (12 steps, 0 failures, 1 skip)

✅ Green to release. No regressions detected.
```

## HP File Structure

HP files live in `happy-path/` in your project and use YAML frontmatter:

```markdown
---
id: HP-001
name: User Login
status: active
created: 2026-02-22
updated: 2026-02-22
author: qa-engineer
priority: P0
tags: [authentication, login]
---

# HP-001: User Login

## Overview
Validates that a registered user can log in with correct credentials.

## Prerequisites
- [ ] App is running at [base-url]
- [ ] Test user account exists

## Test Steps

### Step 1: Navigate to Login
**Action**: GET /login
**Expected**: HTTP 200, login form rendered
**Actual**: [ ] Pass / [ ] Fail

...
```

## BUG Report Structure

BUG files are auto-generated during bug-hunt and regression runs:

```markdown
---
bug-id: BUG-001
severity: P0
status: open
found-by: qa-engineer
found-date: 2026-02-22
component: Account / Order History
---

# BUG-001: /account/orders returns 500

## Severity
P0 — All logged-in users cannot view order history.

## Evidence
```
curl -s http://localhost:3000/account/orders
HTTP 500: {"message":"Cannot read properties of undefined"}
```

...
```

## Integration with Other Agents

| Agent | How They Work Together |
|-------|----------------------|
| **CEO** | Delegates pre-release go/no-go decisions and quality questions to qa-engineer |
| **Product Manager** | Identifies P0/P1 flows that QA should prioritize; qa-engineer validates PM's acceptance criteria |
| **AI Specialist** | Handles prompt/token optimization; qa-engineer handles functional correctness |
| **Financial Advisor** | QA surfaces revenue-impacting bugs (checkout broken, payment errors) for financial risk assessment |

## Installation

```bash
/plugin install qa-engineer@jontoio-claude-agents
```

Or manually: copy this folder into your Claude plugins directory.

## Best Practices

1. **Run `quick-health-check` first** — before any deeper investigation, confirm the app is reachable
2. **Start HP files as `draft`** — never activate without human review; the agent's step inference may miss context
3. **Version-control `happy-path/`** — it belongs in the repo, committed alongside code changes
4. **Create HP files after bug fixes** — every fixed bug should have an HP to prevent recurrence
5. **Run regression before every release** — even minor releases can have unexpected side effects
6. **Focus P0 HPs on revenue flows** — checkout, auth, and data integrity are always P0

## Limitations

- Cannot execute JavaScript in a browser — console error detection is static analysis only
- Endpoint testing via curl may not replicate complex authenticated sessions
- HP files describe intent — actual validation depends on the environment being reachable
- Does not replace a dedicated automated test suite (Playwright, Cypress, Jest) — HP files are living documentation complementing, not replacing, automated tests

## Examples

- [`ecommerce-checkout-qa.md`](./examples/ecommerce-checkout-qa.md) — Full walkthrough: happy path mapping → bug hunt → regression on a Next.js e-commerce app

## Support

- Issues: https://github.com/jontoIO/claude-agents/issues
- Documentation: https://github.com/jontoIO/claude-agents
- Contributing: See [CONTRIBUTING.md](../../CONTRIBUTING.md)

## License

MIT — See [LICENSE](../../LICENSE)
