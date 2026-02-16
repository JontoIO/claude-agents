# Quick Test Plan Command

Adds a comprehensive test strategy to the current plan in 3-5 minutes, including automated tests, manual checkpoints, edge cases, and success criteria.

## Purpose

Rapidly add testing coverage when:
- Implementation plan lacks test strategy
- Need to add verification steps to existing plan
- Want to ensure quality without lengthy planning
- Responding to "how do we test this?" questions
- Quick test coverage before starting implementation

## When to Use

**Use quick-test-plan when**:
- Need test strategy in 3-5 minutes
- Working on single feature or component
- Plan exists but lacks verification steps
- Want basic coverage (unit + integration + manual)
- Fast iteration, can refine tests later

**Use full test-strategy-design skill when**:
- Need comprehensive test analysis (gap analysis, 26+ tests)
- Planning complex multi-component feature
- Designing E2E test suite
- Performance and load testing needed
- Creating detailed test documentation

## Command Format

```bash
/quick-test-plan
```

Analyzes current plan/task and adds test strategy.

## Examples

### Example 1: Add Tests to Feature Plan

**Current Plan**:
```
Feature: Add dark mode support

Implementation:
1. Add theme context provider
2. Create theme toggle component
3. Update all components to use theme colors
4. Add localStorage persistence
```

**Command**:
```bash
/quick-test-plan
```

**Output Added to Plan**:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TEST STRATEGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Automated Tests (12 tests, ~4 hours)

### Unit Tests (5 tests)
✅ Theme context provides light/dark values
✅ Theme toggle switches between modes
✅ localStorage saves/loads theme preference
✅ Theme colors map correctly (light → #fff, dark → #1a1a1a)
✅ Invalid theme value fallsback to light

### Integration Tests (4 tests)
✅ Theme toggle updates all components
✅ Page reload restores saved theme
✅ Theme changes persist across sessions
✅ System preference detection works (prefers-color-scheme)

### Component Tests (3 tests)
✅ All 15 components render in dark mode without errors
✅ Text contrast meets WCAG AAA standards
✅ Icons and images adapt to theme

**Commands**:
```bash
npm run test:unit        # Run unit tests
npm run test:integration # Run integration tests
npm run test:components  # Run component tests
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Manual Testing Checklist (~30 min)

### Functional Testing
- [ ] Toggle theme from light → dark → light
- [ ] Verify all pages render correctly in dark mode
- [ ] Check localStorage contains theme preference
- [ ] Close/reopen browser, theme persists
- [ ] Test on 3 major browsers (Chrome, Firefox, Safari)

### Visual Testing
- [ ] No white flashes during theme switch
- [ ] All text readable (sufficient contrast)
- [ ] Images and icons look appropriate
- [ ] Buttons and inputs styled correctly
- [ ] No UI elements "disappear" in dark mode

### Edge Cases
- [ ] First visit (no saved preference) → Uses system preference
- [ ] System preference = dark, user chooses light → User choice wins
- [ ] Rapid toggle (click toggle 10x quickly) → No UI glitches
- [ ] localStorage full/disabled → Gracefully falls back to default

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Success Criteria

**Definition of Done**:
- ✅ All 12 automated tests pass
- ✅ Manual testing checklist completed (12/12 items)
- ✅ No visual regressions in dark mode
- ✅ WCAG AAA contrast ratio achieved (4.5:1 minimum)
- ✅ Theme persists across sessions in 3 browsers
- ✅ No console errors in either theme

**Quality Gates**:
- All P0 tests pass (required to merge)
- No critical (P0) bugs found
- Code coverage ≥ 80% for new theme code

**Performance Targets**:
- Theme switch completes in <100ms
- No layout shift during theme change

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Implementation Guidance

**Test-Driven Approach**:
1. Write unit tests for theme context (30 min)
2. Implement theme context to pass tests
3. Write component tests for theme toggle (20 min)
4. Implement toggle component
5. Write integration tests (40 min)
6. Integrate theme across all components
7. Run manual testing checklist (30 min)

**Testing Timeline**:
- Automated tests: 4 hours (parallel with implementation)
- Manual testing: 30 minutes (after implementation)
- Total: 4.5 hours

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Test Strategy Added ✓ (Generated in 4 minutes)

For more comprehensive testing: /test-strategy-design
```

### Example 2: Add Tests to API Endpoint Plan

**Current Plan**:
```
Feature: Add bulk delete endpoint

Implementation:
1. Create POST /api/bulk-delete endpoint
2. Validate user permissions for all items
3. Execute delete in transaction
4. Return success/failure response
```

**Command**:
```bash
/quick-test-plan
```

**Output Added**:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TEST STRATEGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Automated Tests (10 tests, ~3 hours)

### Unit Tests (4 tests)
✅ Permission validation: User owns all items → allowed
✅ Permission validation: User owns none → denied
✅ Permission validation: User owns some → denied (all-or-nothing)
✅ Transaction: One item fails → all rollback

### Integration Tests (6 tests)
✅ Bulk delete 10 items → all deleted, 200 response
✅ Bulk delete with invalid item ID → 400 error
✅ Bulk delete without auth → 401 error
✅ Bulk delete someone else's items → 403 error
✅ Bulk delete 1000 items → queued as background job
✅ Transaction rollback: Database error → no items deleted

**Commands**:
```bash
pytest tests/test_bulk_delete.py  # Run all tests
pytest tests/ -k "bulk_delete"     # Run by keyword
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Manual Testing Checklist (~20 min)

### Happy Path
- [ ] Delete 5 items → All removed, success message
- [ ] Check database → Items actually deleted
- [ ] Verify audit log → Deletion recorded

### Error Scenarios
- [ ] Try delete without permission → Clear error message
- [ ] Try delete invalid ID → Appropriate error
- [ ] Try delete 0 items → Handled gracefully
- [ ] Try delete with malformed request → 400 error

### Edge Cases
- [ ] Delete 1 item → Works (no special case bug)
- [ ] Delete 500 items → Completes in <30 seconds
- [ ] Rapid deletions (2 requests same items) → Second fails appropriately

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Success Criteria

**Definition of Done**:
- ✅ All 10 automated tests pass
- ✅ Manual testing checklist completed (11/11 items)
- ✅ Transaction integrity verified (rollback works)
- ✅ Permissions enforced (no unauthorized deletes)
- ✅ Error messages clear and actionable

**Quality Gates**:
- All security tests pass (permissions, auth)
- Transaction tests pass (data integrity)
- No P0 bugs

**Performance Targets**:
- 100 items: <5 seconds
- 1000 items: Queued, completes in <1 minute

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Test Strategy Added ✓ (Generated in 3 minutes)
```

### Example 3: Add Tests to Bug Fix Plan

**Current Plan**:
```
Bug Fix: Search results not showing for queries with special characters

Investigation:
- Issue: Queries with "&", "$", "%" fail
- Root cause: Search query not properly escaped

Fix:
1. Add query escaping function
2. Apply to all search inputs
3. Test with special characters
```

**Command**:
```bash
/quick-test-plan
```

**Output Added**:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TEST STRATEGY (Bug Fix Verification)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## Automated Tests (6 tests, ~1.5 hours)

### Unit Tests (4 tests)
✅ Query escape: "&" → properly escaped
✅ Query escape: "$" → properly escaped
✅ Query escape: "%" → properly escaped
✅ Query escape: Multiple special chars → all escaped

### Integration Tests (2 tests)
✅ Search "user & admin" → Returns results (was failing)
✅ Search "$price" → Returns results (was failing)

**Commands**:
```bash
npm run test:search  # Run search tests
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Manual Testing Checklist (~15 min)

### Reproduce Original Bug
- [ ] Search "user & admin" → Returns results (should work now)
- [ ] Search "$100" → Returns results (should work now)
- [ ] Search "50%" → Returns results (should work now)

### Regression Testing
- [ ] Search normal query "hello" → Still works
- [ ] Search with spaces "hello world" → Still works
- [ ] Empty search → Handled gracefully

### Edge Cases
- [ ] Search only special chars "&$%" → No crash
- [ ] Search very long query with special chars → Works
- [ ] Search with unicode + special chars → Works

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Regression Prevention

**Add to Test Suite**:
- Save original bug scenarios as permanent tests
- Prevents re-introduction in future refactors

```javascript
// New regression test
test('search handles special characters', () => {
  expect(search('user & admin')).toHaveResults();
  expect(search('$100')).toHaveResults();
  expect(search('50%')).toHaveResults();
});
```

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
## Success Criteria

**Definition of Done**:
- ✅ All 6 automated tests pass
- ✅ Original bug scenarios verified fixed
- ✅ Regression tests added (prevents reoccurrence)
- ✅ No new bugs introduced (normal queries still work)

**Quality Gates**:
- Reproduce original bug → Fixed ✓
- All regression tests pass
- No performance degradation

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Test Strategy Added ✓ (Generated in 3 minutes)
```

## Test Plan Components

Every quick test plan includes:

### 1. Automated Tests
- **Unit Tests**: Pure logic, no dependencies
- **Integration Tests**: Multi-component, database, API
- **Component Tests**: UI components (if frontend)
- Test commands to run tests

### 2. Manual Testing Checklist
- **Functional**: Core workflows
- **Error Scenarios**: Error handling
- **Edge Cases**: Boundary conditions, unusual inputs
- Checkboxes for tracking progress

### 3. Success Criteria
- **Definition of Done**: What "passing" means
- **Quality Gates**: Required to merge
- **Performance Targets**: Speed/efficiency goals

### 4. Implementation Guidance (Optional)
- Testing timeline
- Test-driven approach
- Integration with CI/CD

## Testing Principles Applied

### Comprehensive Coverage
```
✓ Happy path (core functionality)
✓ Error scenarios (validation, auth)
✓ Edge cases (0 items, max items, special chars)
✓ Regression (doesn't break existing features)
✓ Performance (meets speed targets)
```

### Balanced Approach
```
Automated (fast, repeatable):
  - Unit tests for logic
  - Integration tests for workflows
  - Component tests for UI

Manual (human judgment):
  - Exploratory testing
  - Usability assessment
  - Visual verification
```

### Clear Success Criteria
```
✓ Specific: "All 10 tests pass" not "tests pass"
✓ Measurable: "80% coverage" not "good coverage"
✓ Achievable: Realistic targets
✓ Time-bound: Part of definition of done
```

## Customization

The command adapts based on context:

### Feature Type Detection
- **Frontend feature** → Add component + visual tests
- **Backend API** → Add integration + security tests
- **Bug fix** → Add regression tests
- **Performance work** → Add performance benchmarks

### Complexity Adjustment
- **Simple feature** → 5-8 tests
- **Medium feature** → 10-15 tests
- **Complex feature** → Suggest full test-strategy-design skill

## Integration with Development

### Pre-Implementation
```bash
# Add test plan before coding
/quick-test-plan

# Now implement with clear testing goals
```

### Test-Driven Development
```
Use test list as TDD guide:
1. Write first test from list
2. Implement feature to pass test
3. Repeat for all tests
```

### CI/CD Integration
```
Add to PR checklist:
- [ ] All automated tests pass
- [ ] Manual testing checklist completed
- [ ] Success criteria met
```

## Common Use Cases

### Adding Tests to Existing Plan
```bash
# You have implementation plan, need tests
/quick-test-plan
```

### Bug Fix Verification
```bash
# Ensure bug is fixed and won't regress
/quick-test-plan
```

### Pre-Implementation Planning
```bash
# Define tests before coding
/quick-test-plan
```

## Tips for Better Test Plans

1. **Run early**: Add tests to plan before starting implementation
2. **Use as TDD guide**: Implement tests first, then code
3. **Track progress**: Check off tests as you complete them
4. **Adapt as needed**: Add tests if you discover edge cases
5. **Automate what you can**: Manual tests only for what can't be automated

## Integration with Other Commands

- **quick-test-plan** - This command (rapid test addition)
- **quick-instruction-audit** - Ensure test instructions are clear
- **/test-strategy-design** - Full comprehensive test design (26+ tests)

---

**Remember**: Quick test plans provide 80% coverage in 20% time. Use them for fast iteration, refine with full skill if needed.
