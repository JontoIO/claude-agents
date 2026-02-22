# Suggest Happy Paths Command

Analyzes the codebase (new features, bug reports, coverage gaps) to propose new HP files. Presents candidates to the user and creates files only after explicit confirmation.

## Purpose

Use this command when:
- New features were recently added and need QA coverage
- A bug was fixed and you want a regression HP to prevent recurrence
- You want to expand coverage beyond existing HP files
- You want QA to proactively surface what flows are missing documentation

## Command Format

```bash
/qa-engineer:suggest-happy-paths
/qa-engineer:suggest-happy-paths "[scope description]"
/qa-engineer:suggest-happy-paths --from-bug "[bug description or BUG-ID]"
/qa-engineer:suggest-happy-paths --recent-changes
/qa-engineer:suggest-happy-paths --coverage-gaps
```

### Parameters

```bash
"[scope]"           # Focus suggestion on a specific feature or domain
--from-bug "[desc]" # Suggest HPs that would have caught a specific bug
--recent-changes    # Analyze git log for recently added/changed files
--coverage-gaps     # Compare routes vs existing HP files to find uncovered flows
```

## Examples

### General Suggestion (no scope)
```bash
/qa-engineer:suggest-happy-paths
```
Analyzes all sources: recent git changes, coverage gaps, related flows.

### Scoped to Feature
```bash
/qa-engineer:suggest-happy-paths "checkout flow"
```
Focuses on checkout-related routes and flows only.

### From a Bug Report
```bash
/qa-engineer:suggest-happy-paths --from-bug "Payment fails for EU users when VAT is applied"
```
Suggests HPs that would cover the broken scenario and adjacent edge cases.

### From Recent Git Changes
```bash
/qa-engineer:suggest-happy-paths --recent-changes
```
Runs `git log --since="7 days ago" --name-only` to find changed files, then suggests HPs for affected flows.

### Coverage Gap Analysis
```bash
/qa-engineer:suggest-happy-paths --coverage-gaps
```
Compares all discovered routes vs existing HP files, lists uncovered flows sorted by priority.

---

## Execution Steps

### Step 1: Source Analysis

Depending on flags, analyze one or more sources:

**New Features** (always active):
```bash
git log --since="14 days ago" --name-only --pretty=format:""
```
Filter to routing/controller/handler files. Extract affected flows.

**Bug Report Analysis** (`--from-bug`):
- Parse the bug description for: affected route, user action, data type
- Suggest: HP for the exact bug scenario + HP for adjacent flows (same component)

**Coverage Gap Analysis** (`--coverage-gaps` or always secondary):
- Glob all routing files, extract all routes
- Read all existing HP files from `happy-path/INDEX.md`
- Diff: routes with no HP → sorted by priority (auth/payment routes = P0)

**Related Flows** (always active as supplement):
- For each existing HP file, check "Related Flows" section
- Suggest HPs for related flows not yet documented

### Step 2: Candidate List

Present a numbered list of proposed HP files:

```
## Suggested Happy Paths

Found [N] candidates from: [sources analyzed]

| # | Proposed HP | Priority | Source | Reason |
|---|-------------|----------|--------|--------|
| 1 | User Password Reset | P0 | Coverage gap | /auth/reset-password route has no HP |
| 2 | EU VAT Checkout | P1 | --from-bug | Would have caught BUG-042: VAT calculation error |
| 3 | Guest Checkout | P1 | Coverage gap | /checkout route covered but guest flow is not |
| 4 | Order History Pagination | P2 | Recent changes | GET /api/orders?page= added in last 7 days |
| 5 | Admin: Bulk User Export | P3 | Coverage gap | /admin/export route uncovered |

**Note**: These are proposals only. No files will be created until you confirm.
```

### Step 3: User Confirmation

Use `AskUserQuestion` to ask:
- Which candidates to create (can select all, subset, or none)
- Whether to create as `draft` (default) or `active`
- Target directory for the `happy-path/` folder (if not yet established)

### Step 4: HP File Creation

For each confirmed candidate:
1. Generate full HP file content using the template (from happy-path-mapping SKILL.md)
2. Assign next sequential HP-XXX ID
3. Set `status: draft`
4. Write to `happy-path/HP-XXX.md`
5. Update `happy-path/INDEX.md`

### Step 5: Creation Summary

```
## Created [N] Happy Path Files

| ID | Name | Priority | File |
|----|------|----------|------|
| HP-007 | User Password Reset | P0 | happy-path/HP-007.md |
| HP-008 | EU VAT Checkout | P1 | happy-path/HP-008.md |

**Status**: All created as `draft` — review and update step details, then change to `active`.

**Recommended next step**: Run `happy-path-mapping` to fill in specific test steps for the new HPs, or review them manually and activate when ready.
```

---

## Output Format

The command always ends with a clear action summary:
- Number of candidates analyzed
- Number of HPs created vs declined
- Any HPs that need manual step-filling (where specific actions couldn't be inferred from code)
- Recommended next command

---

## Tips

- Run `--recent-changes` after every sprint to ensure new features get QA coverage immediately
- Run `--from-bug` whenever a bug is fixed — the fix isn't complete until there's an HP preventing recurrence
- Run `--coverage-gaps` quarterly to catch flows that were added without going through QA
- Use scoped suggestions (e.g., `"payment flow"`) when focused on a specific area — avoids noise from unrelated suggestions

## Limitations

- Cannot suggest HPs for UI interactions that have no corresponding route (e.g., pure client-side state changes)
- `--recent-changes` requires git history — won't work on a fresh clone with a single commit
- Suggestions are based on code analysis; domain knowledge from the user may identify additional flows not visible in code
