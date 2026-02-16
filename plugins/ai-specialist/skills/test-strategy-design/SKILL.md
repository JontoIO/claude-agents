---
name: test-strategy-design
description: Add comprehensive verification strategies to plans using 5-step framework including test gap analysis, automated test design, manual checkpoints, edge cases, and success criteria to achieve 100% test coverage
---

# Test Strategy Design Skill

Analyze implementation plans and add comprehensive verification strategies (automated tests + manual checkpoints + edge cases + success criteria) to ensure quality and catch issues before production.

## When to Use This Skill

Use this skill when you need to:
- Add test strategies to implementation plans that lack verification
- Design comprehensive test coverage for new features
- Identify testing gaps in existing plans
- Create both automated and manual testing approaches
- Define edge cases and success criteria
- Ensure implementations include verification at every step
- Prevent "implementation without testing" scenarios

## 5-Step Test Strategy Design Framework

### Step 1: Context Discovery (5 min)

**Objective**: Understand what's being built and current test coverage

**Actions**:
1. **Read Current Plan/Task**:
   - Identify features being implemented
   - List components affected (frontend, backend, database, API, etc.)
   - Note integration points and dependencies
   - Understand user-facing vs internal changes
2. **Analyze Existing Tests**:
   - Check for existing test files (test/, __tests__, spec/, *.test.*)
   - Review test framework in use (Jest, Pytest, RSpec, etc.)
   - Assess current test coverage (if metrics available)
   - Identify test patterns (unit, integration, e2e)
3. **Identify Risk Areas**:
   - Critical paths (auth, payments, data loss scenarios)
   - Complex logic (algorithms, business rules)
   - Integration points (APIs, databases, third-party services)
   - User-facing features (UI, workflows)

**Output Format**:
```markdown
## Context Discovery

### Implementation Scope
**Feature**: Add bulk operations to allow users to select and act on multiple items
**Components Affected**:
- Frontend: Checkbox selection UI, bulk action menu
- Backend: Bulk operation endpoints, background job processing
- Database: Transaction handling for multiple records
- API: New POST /api/bulk-actions endpoint

**Integration Points**:
- Background job queue (Celery/Sidekiq)
- Database transaction management
- Frontend state management (Redux/Zustand)
- Permissions system (verify user can act on all selected items)

**User-Facing Changes**:
- New checkbox column in item list
- Bulk action dropdown menu
- Progress indicator for bulk operations
- Success/error notifications

### Existing Test Infrastructure
**Test Framework**: Jest (frontend), Pytest (backend)
**Test Files Found**:
- Frontend: 24 test files, ~600 tests
- Backend: 18 test files, ~320 tests

**Current Coverage** (from last report):
- Frontend: 72% line coverage
- Backend: 85% line coverage

**Test Patterns in Use**:
- Unit tests for utility functions
- Integration tests for API endpoints
- Component tests for React components
- No E2E tests currently

### Risk Areas
**Critical Paths**:
1. **Permissions**: User must have permission for ALL selected items (bulk delete shouldn't allow deleting items user can't access)
2. **Data Integrity**: Partial failures must not leave data in inconsistent state
3. **Performance**: Bulk operations on 1000+ items must not timeout or crash

**Complex Logic**:
1. Transaction handling (all-or-nothing vs partial success)
2. Background job retry logic
3. Permission aggregation across multiple items

**Integration Points**:
1. Background job queue (must handle job failures gracefully)
2. Database (must use transactions correctly)
3. Frontend state (must update UI correctly after bulk operation)

**User-Facing Risks**:
1. Confusing UI if permissions vary across selected items
2. No feedback if bulk operation takes >5 seconds
3. Unclear error messages if some items fail
```

---

### Step 2: Test Gap Analysis (8 min)

**Objective**: Identify missing test coverage in the current plan

**Actions**:
1. **Review Plan for Test Mentions**:
   - Check if plan includes testing steps
   - Note what's tested vs not tested
   - Identify implicit testing assumptions
2. **Map Components to Tests**:
   - For each component, list what should be tested
   - Identify components with no test strategy
   - Flag integration points lacking integration tests
3. **Categorize Gaps**:
   - **Missing Automated Tests**: Unit, integration, E2E
   - **Missing Manual Tests**: Exploratory, usability, edge cases
   - **Missing Success Criteria**: No definition of "done"
   - **Missing Edge Cases**: Error scenarios, boundary conditions
4. **Prioritize Gaps**:
   - **P0 (Critical)**: Tests for critical paths, data integrity, security
   - **P1 (High)**: Tests for core functionality, user workflows
   - **P2 (Medium)**: Tests for edge cases, error handling
   - **P3 (Nice-to-have)**: Performance tests, stress tests, chaos engineering

**Output Format**:
```markdown
## Test Gap Analysis

### Current Plan Test Coverage

**Plan Mentions**:
- ✅ "Test the bulk operation endpoint with 10 items"
- ✅ "Verify UI updates after bulk action"
- ❌ No mention of permission testing
- ❌ No mention of error handling tests
- ❌ No mention of performance/scale testing
- ❌ No E2E tests planned
- ❌ No manual testing checklist

**Coverage Assessment**: 20% (2/10 critical areas have tests)

### Component Test Mapping

**Frontend Components**:
1. **Checkbox Selection UI**
   - Current: ❌ No tests mentioned
   - Needed: Component test (select all, select individual, deselect, disabled state)
2. **Bulk Action Menu**
   - Current: ❌ No tests mentioned
   - Needed: Component test (menu open/close, action selection, disabled when nothing selected)
3. **Progress Indicator**
   - Current: ❌ No tests mentioned
   - Needed: Component test (shows during operation, updates progress, hides on complete)
4. **Success/Error Notifications**
   - Current: ✅ "Verify UI updates"
   - Gap: No specific test for partial failures (some items succeed, some fail)

**Backend Components**:
1. **POST /api/bulk-actions Endpoint**
   - Current: ✅ "Test endpoint with 10 items"
   - Gap: No test for 1000+ items, no permission test, no error scenarios
2. **Background Job Processing**
   - Current: ❌ No tests mentioned
   - Needed: Integration test (job enqueued, job processes items, job handles failures)
3. **Transaction Management**
   - Current: ❌ No tests mentioned
   - Needed: Integration test (all-or-nothing behavior, rollback on error)
4. **Permissions Check**
   - Current: ❌ No tests mentioned
   - Needed: Unit + integration test (verify user can act on all items)

### Test Gaps by Category

**Missing Automated Tests**:
1. **Unit Tests** (8 gaps):
   - Permission validation logic (is user allowed to act on all selected items?)
   - Bulk action transaction logic (all-or-nothing vs partial)
   - Error message generation (clear messages for different failure types)
   - Selection state management (select/deselect/select-all logic)
   - Progress calculation (% complete based on items processed)
   - [3 more...]

2. **Integration Tests** (6 gaps):
   - Bulk operation endpoint with permission check
   - Background job with database transaction
   - API → Background job → Database flow
   - Partial failure handling (some items succeed, some fail)
   - Retry logic for failed items
   - [1 more...]

3. **E2E Tests** (4 gaps):
   - Complete user workflow: Select items → Choose action → See progress → Verify results
   - Error scenario: Select items user can't act on → See error message
   - Performance scenario: Bulk operation with 500 items → Completes in <30s
   - Partial failure scenario: 10 items, 2 fail → See clear error for failed items

**Missing Manual Tests** (5 gaps):
1. Exploratory testing: Try to break the feature with unusual selections
2. Usability testing: Is the UI intuitive? Are error messages clear?
3. Cross-browser testing: Works in Chrome, Firefox, Safari, Edge?
4. Mobile testing: Works on mobile screens?
5. Accessibility testing: Keyboard navigation, screen reader support

**Missing Success Criteria** (3 gaps):
1. No definition of "passing" (all tests pass? 80% coverage? 0 bugs?)
2. No performance target (how fast should bulk operations complete?)
3. No quality bar (P0 bugs = blocker? P1 bugs = acceptable?)

**Missing Edge Cases** (12 gaps):
1. Select 0 items → Bulk action button disabled
2. Select 1 item → Bulk action works (no special case needed)
3. Select 10,000 items → UI doesn't freeze, operation handles gracefully
4. Select items with mixed permissions → Clear error or filter out unauthorized
5. Operation fails mid-way → Database in consistent state (rollback or partial success handling)
6. User navigates away during operation → Operation continues or cancels gracefully
7. Network error during operation → Retry or clear error message
8. Background job dies → Job requeued or marked as failed
9. [4 more edge cases...]

### Priority Classification

**P0 (Critical - Must Have)**:
- Permission validation tests (security risk)
- Transaction integrity tests (data corruption risk)
- E2E happy path test (core functionality)
- Error handling tests (user experience)

**P1 (High - Should Have)**:
- Edge case tests (0 items, 1 item, many items)
- Partial failure handling test
- Performance test (500 items)
- Manual usability testing

**P2 (Medium - Nice to Have)**:
- Accessibility tests
- Cross-browser tests
- Stress tests (10,000 items)

**P3 (Low - Optional)**:
- Chaos testing (random failures)
- Load testing (concurrent bulk operations)

### Gap Summary

| Category | Gaps | P0 | P1 | P2 | P3 |
|----------|------|----|----|----|----|
| Unit Tests | 8 | 2 | 4 | 2 | 0 |
| Integration Tests | 6 | 3 | 2 | 1 | 0 |
| E2E Tests | 4 | 1 | 2 | 1 | 0 |
| Manual Tests | 5 | 0 | 2 | 3 | 0 |
| Edge Cases | 12 | 4 | 6 | 2 | 0 |
| Success Criteria | 3 | 3 | 0 | 0 | 0 |
| **Total** | **38 gaps** | **13** | **16** | **9** | **0** |

**Current Coverage**: 2/40 areas tested (5%)
**Target Coverage**: 29/40 areas tested (73% - all P0+P1 gaps filled)
```

---

### Step 3: Test Strategy Design (10 min)

**Objective**: Design automated tests, manual checkpoints, and edge case coverage

**Actions**:
1. **Automated Test Design**:
   - **Unit Tests**: Pure function/class tests, no external dependencies
   - **Integration Tests**: Multi-component tests, database/API interactions
   - **E2E Tests**: Full user workflow tests, browser automation
   - For each test: Write test name, input, expected output, assertion
2. **Manual Test Design**:
   - **Functional Testing**: Step-by-step user workflows to verify manually
   - **Exploratory Testing**: Free-form testing to find unexpected issues
   - **Usability Testing**: Assess user experience, clarity, intuitive design
   - For each: Write test scenario, steps, expected result
3. **Edge Case Design**:
   - **Boundary Conditions**: 0 items, 1 item, max items, empty states
   - **Error Scenarios**: Network errors, permission errors, validation errors
   - **Race Conditions**: Concurrent operations, state conflicts
   - For each: Describe scenario, expected behavior, test approach
4. **Performance Test Design**:
   - Define performance targets (response time, throughput)
   - Design load tests for expected and peak traffic
   - Identify performance bottlenecks to monitor

**Output Format**:
```markdown
## Test Strategy Design

### Automated Tests

#### Unit Tests (8 tests)

**Test 1: Permission Validation - User has permission for all items**
```python
def test_bulk_permission_all_allowed():
    user = User(id=1, permissions=['delete_item'])
    items = [Item(id=1, owner=user), Item(id=2, owner=user)]

    result = validate_bulk_permissions(user, items, 'delete')

    assert result.allowed == True
    assert result.unauthorized_items == []
```

**Test 2: Permission Validation - User lacks permission for some items**
```python
def test_bulk_permission_mixed():
    user = User(id=1, permissions=['delete_item'])
    items = [Item(id=1, owner=user), Item(id=2, owner=other_user)]

    result = validate_bulk_permissions(user, items, 'delete')

    assert result.allowed == False
    assert result.unauthorized_items == [2]
    assert result.error_message == "You don't have permission to delete 1 item(s)"
```

**Test 3: Bulk Operation Transaction - All succeed**
```python
def test_bulk_operation_transaction_success():
    items = [Item(id=1), Item(id=2), Item(id=3)]

    with mock_transaction():
        result = bulk_delete(items)

    assert result.success == True
    assert result.deleted_count == 3
    assert Item.count() == 0  # All deleted
```

**Test 4: Bulk Operation Transaction - One fails, all rollback**
```python
def test_bulk_operation_transaction_rollback():
    items = [Item(id=1), Item(id=2), Item(id=3, locked=True)]

    with mock_transaction():
        result = bulk_delete(items)

    assert result.success == False
    assert result.error == "Cannot delete locked item 3"
    assert Item.count() == 3  # All still exist (rollback)
```

**Test 5: Selection State - Select all**
```javascript
test('select all checkbox selects all visible items', () => {
  render(<ItemList items={[item1, item2, item3]} />);

  fireEvent.click(screen.getByLabelText('Select all'));

  expect(screen.getByLabelText('Select item 1')).toBeChecked();
  expect(screen.getByLabelText('Select item 2')).toBeChecked();
  expect(screen.getByLabelText('Select item 3')).toBeChecked();
});
```

**Test 6: Progress Calculation - 60% complete**
```python
def test_progress_calculation():
    total_items = 100
    processed_items = 60

    progress = calculate_progress(processed_items, total_items)

    assert progress.percentage == 60
    assert progress.remaining == 40
    assert progress.estimated_time == 20  # Based on current rate
```

[2 more unit tests...]

#### Integration Tests (6 tests)

**Test 1: Bulk Endpoint with Permission Check**
```python
def test_bulk_delete_endpoint_with_permissions():
    user = authenticate(token)
    items = [1, 2, 3]  # User owns 1 and 2, not 3

    response = client.post('/api/bulk-actions',
                          json={'action': 'delete', 'items': items},
                          headers={'Authorization': f'Bearer {token}'})

    assert response.status_code == 403
    assert response.json['error'] == "Missing permission for 1 item(s)"
    assert Item.exists(1) and Item.exists(2) and Item.exists(3)  # None deleted
```

**Test 2: Bulk Endpoint to Background Job**
```python
def test_bulk_operation_enqueues_background_job():
    user = authenticate(token)
    items = [1, 2, 3]

    response = client.post('/api/bulk-actions',
                          json={'action': 'delete', 'items': items},
                          headers={'Authorization': f'Bearer {token}'})

    assert response.status_code == 202  # Accepted
    assert response.json['job_id'] is not None
    assert background_queue.length() == 1
    assert background_queue.peek()['action'] == 'delete'
```

**Test 3: Background Job Processes Items**
```python
def test_background_job_processes_bulk_delete():
    job = BulkJob(action='delete', items=[1, 2, 3], user_id=1)

    process_bulk_job(job)

    assert job.status == 'completed'
    assert job.processed_count == 3
    assert job.success_count == 3
    assert Item.count() == 0
```

**Test 4: Partial Failure Handling**
```python
def test_bulk_job_partial_failure():
    items = [Item(id=1), Item(id=2, locked=True), Item(id=3)]
    job = BulkJob(action='delete', items=[1, 2, 3])

    process_bulk_job(job)

    assert job.status == 'partial'
    assert job.success_count == 2
    assert job.failure_count == 1
    assert job.errors == {2: "Cannot delete locked item"}
    assert Item.exists(2) and not Item.exists(1) and not Item.exists(3)
```

[2 more integration tests...]

#### E2E Tests (4 tests)

**Test 1: Happy Path - Bulk Delete**
```javascript
test('user can select multiple items and bulk delete', async () => {
  // Setup: Login and navigate to items page
  await page.goto('/items');
  await page.login('test@example.com', 'password');

  // Select 3 items
  await page.click('[data-testid="item-1-checkbox"]');
  await page.click('[data-testid="item-2-checkbox"]');
  await page.click('[data-testid="item-3-checkbox"]');

  // Open bulk actions and select delete
  await page.click('[data-testid="bulk-actions-menu"]');
  await page.click('[data-testid="bulk-delete-action"]');

  // Confirm deletion
  await page.click('[data-testid="confirm-delete"]');

  // Wait for progress indicator
  await page.waitForSelector('[data-testid="bulk-progress"]');

  // Wait for completion
  await page.waitForSelector('[data-testid="success-notification"]');

  // Verify items deleted
  expect(await page.$$('[data-testid^="item-"]')).toHaveLength(0);
  expect(await page.textContent('[data-testid="success-notification"]'))
    .toBe('3 items deleted successfully');
});
```

**Test 2: Error Scenario - Mixed Permissions**
```javascript
test('user sees error when lacking permission for some items', async () => {
  await page.goto('/items');
  await page.login('user-limited@example.com', 'password');

  // Select own item and someone else's item
  await page.click('[data-testid="item-1-checkbox"]');  // User owns
  await page.click('[data-testid="item-99-checkbox"]'); // Other user owns

  await page.click('[data-testid="bulk-actions-menu"]');
  await page.click('[data-testid="bulk-delete-action"]');
  await page.click('[data-testid="confirm-delete"]');

  // Expect error notification
  await page.waitForSelector('[data-testid="error-notification"]');
  expect(await page.textContent('[data-testid="error-notification"]'))
    .toContain("You don't have permission to delete 1 item");

  // Verify nothing deleted
  expect(await page.$$('[data-testid^="item-"]')).toHaveLength(2);
});
```

[2 more E2E tests...]

### Manual Test Checklist

#### Functional Testing

**Test Scenario 1: Basic Bulk Operation Flow**
1. Navigate to items page
2. Select 5 items using checkboxes
3. Open bulk actions dropdown
4. Select "Delete" action
5. Confirm deletion in modal
6. Observe progress indicator
7. Verify success notification appears
8. Verify 5 items are removed from list

**Expected Result**: All 5 items deleted, success notification shown, UI updates correctly

---

**Test Scenario 2: Select All / Deselect All**
1. Navigate to items page with 20 items
2. Click "Select all" checkbox in header
3. Verify all 20 items are checked
4. Click "Select all" again to deselect
5. Verify all 20 items are unchecked
6. Manually select 3 items
7. Click "Select all"
8. Verify all 20 items now checked (including the 3)

**Expected Result**: Select all/deselect all works correctly, doesn't lose manual selections unexpectedly

---

[3 more functional test scenarios...]

#### Exploratory Testing

**Session 1: Break the Selection Logic (15 min)**
- Try selecting items very quickly (click spam)
- Select, deselect, reselect same item rapidly
- Use keyboard shortcuts if available
- Select while page is still loading
- Select, navigate away, come back (state preserved?)

**Goal**: Find edge cases in selection state management

---

**Session 2: Break the Bulk Operation (15 min)**
- Start bulk operation, immediately start another
- Start bulk operation, close browser tab
- Start bulk operation, logout
- Select max items (1000+), try bulk action
- Mix different item types, try bulk action

**Goal**: Find concurrency issues and error handling gaps

---

[2 more exploratory sessions...]

#### Usability Testing

**Task 1: First-Time User - Can they figure out bulk operations?**
- Recruit 3 users unfamiliar with the feature
- Ask: "Delete these 10 items" (don't explain how)
- Observe: Do they find the checkboxes? The bulk menu? Understand the flow?
- Measure: Time to complete, errors made, satisfaction (1-10)

**Success Criteria**: 2/3 users complete task in <2 min without help, 8+/10 satisfaction

---

[2 more usability tests...]

### Edge Cases

**Edge Case 1: Select 0 Items**
- **Scenario**: User opens bulk actions menu without selecting any items
- **Expected Behavior**: Bulk actions button is disabled, or menu shows "Select items first"
- **Test Approach**: E2E test + manual verification

**Edge Case 2: Select 1 Item**
- **Scenario**: User selects 1 item and uses bulk action
- **Expected Behavior**: Works same as selecting multiple (no special case bug)
- **Test Approach**: Unit test (ensure no division by zero or array issues)

**Edge Case 3: Select 10,000 Items**
- **Scenario**: User selects all items in very large dataset
- **Expected Behavior**: UI doesn't freeze, operation queues as background job, progress updates
- **Test Approach**: Performance test with mock data

**Edge Case 4: Mixed Permissions**
- **Scenario**: User selects items they own + items they don't
- **Expected Behavior**: Clear error message "You don't have permission for 3 items", nothing deleted
- **Test Approach**: Integration test + E2E test

**Edge Case 5: Operation Fails Mid-Way**
- **Scenario**: Delete 100 items, database error on item 50
- **Expected Behavior**: Transaction rollback (all 100 still exist) OR partial success (49 deleted, 51 remain, clear error)
- **Test Approach**: Integration test with mock database error

**Edge Case 6: Network Error During Progress**
- **Scenario**: Bulk operation in progress, user loses internet connection
- **Expected Behavior**: Progress indicator shows error, retry button, or "Complete in background" message
- **Test Approach**: Manual test (disconnect network mid-operation)

**Edge Case 7: User Navigates Away**
- **Scenario**: Start bulk operation, navigate to different page
- **Expected Behavior**: Operation continues in background, notification on completion, or confirmation modal
- **Test Approach**: E2E test (start operation, navigate, verify background job completes)

**Edge Case 8: Concurrent Bulk Operations**
- **Scenario**: User starts bulk delete, immediately starts bulk tag operation
- **Expected Behavior**: Both queued, processed sequentially, or second blocked with "Operation in progress"
- **Test Approach**: Integration test (two API calls in rapid succession)

[4 more edge cases...]

### Performance Tests

**Performance Test 1: 100 Items Benchmark**
- **Target**: <5 seconds total (queue + process)
- **Test**: POST /api/bulk-actions with 100 item IDs
- **Measure**: Response time (queue), job completion time (process)
- **Tool**: pytest-benchmark or locust

**Performance Test 2: 500 Items Stress Test**
- **Target**: <30 seconds total, UI responsive
- **Test**: E2E test with 500 items selected
- **Measure**: Time to completion, browser memory usage, UI responsiveness
- **Tool**: Playwright with performance metrics

**Performance Test 3: Concurrent Users**
- **Target**: 10 users doing bulk operations simultaneously, <10s each
- **Test**: Load test with 10 concurrent bulk operations
- **Measure**: Average response time, error rate, database load
- **Tool**: Locust or k6

### Test Strategy Summary

| Test Type | Count | Priority | Time Estimate |
|-----------|-------|----------|---------------|
| Unit Tests | 8 | P0: 2, P1: 4, P2: 2 | 4 hours |
| Integration Tests | 6 | P0: 3, P1: 2, P2: 1 | 6 hours |
| E2E Tests | 4 | P0: 1, P1: 2, P2: 1 | 6 hours |
| Manual Functional | 5 scenarios | P1: 5 | 2 hours |
| Exploratory | 4 sessions | P1: 2, P2: 2 | 1 hour |
| Usability | 3 tasks | P1: 2, P2: 1 | 3 hours (recruiting + testing) |
| Edge Cases | 12 cases | Covered in above tests | - |
| Performance | 3 tests | P1: 3 | 2 hours |
| **Total** | **26 tests + 12 scenarios** | **P0: 6, P1: 18, P2: 8** | **24 hours** |

**Recommended Scope for MVP**: P0 + P1 tests (24 tests, ~20 hours)
```

---

### Step 4: Integration Recommendations (5 min)

**Objective**: Define when/how/what to test, with clear success criteria

**Actions**:
1. **Test Timing**:
   - When to write tests (TDD, during implementation, after implementation)
   - Test running cadence (on save, pre-commit, CI pipeline)
   - Blocking vs non-blocking tests (which tests must pass to merge)
2. **Test Implementation Guidance**:
   - Which tests to implement first (priority order)
   - How to structure test files (naming, organization)
   - Mocking/fixture strategies
   - Test data management
3. **Success Criteria**:
   - Coverage targets (line coverage %, branch coverage %)
   - Quality gates (all P0 tests pass = required, P1 tests pass = strongly recommended)
   - Performance targets (response time, throughput)
   - Manual test completion checklist
4. **Integration into Development Workflow**:
   - Pre-commit hooks (run unit tests, linting)
   - CI pipeline (run all automated tests, coverage reports)
   - PR checklist (manual tests completed, edge cases considered)
   - Definition of done (all tests pass, no P0 bugs)

**Output Format**:
```markdown
## Integration Recommendations

### Test Implementation Timeline

**During Implementation** (Test-Driven Development):
- Write unit tests BEFORE implementing logic
  - Week 1 Day 1-2: Write Test 1-3 (permission validation), implement logic
  - Week 1 Day 3-4: Write Test 4-6 (transaction, selection state), implement logic
- Benefit: Clarifies requirements, catches issues early, prevents regressions

**During Implementation** (Parallel Development):
- Implement feature and tests simultaneously
  - Frontend: Implement UI components + component tests (Week 1)
  - Backend: Implement endpoints + integration tests (Week 1-2)
- Benefit: Faster than TDD, still ensures coverage

**After Implementation** (Verification):
- Implement feature first, add tests after
  - Implementation: Week 1-2
  - Testing: Week 2-3
  - Risk: May discover issues late, harder to refactor
  - Use case: Spike/prototype work, less critical features

**Recommended Approach for This Feature**: Parallel Development
- Implement + test simultaneously for P0+P1 tests
- Add P2 tests after implementation if time allows

---

### Test Running Strategy

**On Save** (Fast feedback loop, <2s):
- Run unit tests for current file only
- Tool: Jest --watch, pytest --watch
- Benefit: Immediate feedback while coding

**Pre-Commit** (Quality gate, <30s):
- Run all unit tests
- Run linting and formatting checks
- Tool: Husky/lint-staged, pre-commit framework
- Benefit: Prevents broken code from entering repo

**CI Pipeline** (Comprehensive check, <10 min):
- Run all unit tests
- Run all integration tests
- Run E2E tests (smoke tests only in PR, full suite on main)
- Generate coverage report
- Run performance benchmark tests
- Tool: GitHub Actions, GitLab CI, Jenkins
- Benefit: Catch issues before merge

**Nightly** (Thorough validation, <1 hour):
- Run all E2E tests (including slow tests)
- Run full performance test suite
- Run cross-browser tests
- Generate detailed reports
- Tool: Scheduled CI job
- Benefit: Catch regressions without slowing PR feedback

### Test Priority Implementation Order

**Phase 1: P0 Tests (Must Have Before Merge)** - 8 hours
1. Test 2: Permission Validation - Mixed permissions (30 min)
2. Test 4: Transaction Rollback on failure (45 min)
3. Test 7: Permission Check in API endpoint (1 hour)
4. E2E Test 1: Happy path bulk delete (2 hours)
5. E2E Test 2: Error scenario - mixed permissions (1 hour)
6. Integration Test 4: Partial failure handling (1.5 hours)
7. Manual Test Scenario 1: Basic flow (30 min)
8. Manual Test: Verify success criteria met (30 min)

**Phase 2: P1 Tests (Strongly Recommended)** - 12 hours
9. Test 1: Permission Validation - All allowed (30 min)
10. Test 3: Transaction Success (30 min)
11. [Continue with remaining P1 tests...]

**Phase 3: P2 Tests (Nice to Have)** - 4 hours
[P2 tests if time allows...]

### Test File Structure

**Frontend Tests**:
```
src/
  components/
    ItemList/
      ItemList.tsx
      ItemList.test.tsx       ← Component tests
      BulkActions/
        BulkActions.tsx
        BulkActions.test.tsx
  hooks/
    useBulkSelection.ts
    useBulkSelection.test.ts  ← Hook tests
  utils/
    permissions.ts
    permissions.test.ts       ← Utility tests
__tests__/
  e2e/
    bulk-operations.spec.ts   ← E2E tests
```

**Backend Tests**:
```
tests/
  unit/
    test_permissions.py       ← Unit tests
    test_bulk_operations.py
  integration/
    test_bulk_api.py         ← Integration tests
    test_bulk_jobs.py
  performance/
    test_bulk_performance.py  ← Performance tests
```

### Mocking Strategy

**External Services**:
- Database: Use test database or in-memory SQLite
- Background jobs: Mock queue, test synchronously
- Third-party APIs: Use mocks/stubs (nock, responses library)

**Example**:
```python
@pytest.fixture
def mock_background_queue():
    with patch('app.queue.enqueue') as mock:
        mock.return_value = {'job_id': '123'}
        yield mock

def test_bulk_operation_enqueues_job(mock_background_queue):
    result = bulk_delete([1, 2, 3])
    mock_background_queue.assert_called_once()
```

### Test Data Management

**Fixtures**:
- Use factories for generating test data (Factory Boy, Faker)
- Keep fixtures small and focused (3-5 items, not 100)
- Reset database state between tests (transactions, truncate)

**Example**:
```python
@pytest.fixture
def sample_items():
    return [
        Item(id=1, name='Item 1', owner=user1),
        Item(id=2, name='Item 2', owner=user1),
        Item(id=3, name='Item 3', owner=user2),
    ]
```

### Success Criteria

**Coverage Targets**:
- **Unit Test Coverage**: 80%+ line coverage for new code
- **Integration Test Coverage**: All API endpoints tested
- **E2E Test Coverage**: All critical user workflows tested
- **Edge Case Coverage**: All identified edge cases have tests

**Quality Gates** (Required to Merge PR):
- ✅ All P0 tests pass (6 tests)
- ✅ 80%+ unit test coverage for new code
- ✅ Linting and formatting pass
- ✅ Manual testing checklist completed
- ✅ No P0 bugs found

**Quality Goals** (Strongly Recommended):
- ✅ All P1 tests pass (18 tests)
- ✅ 90%+ unit test coverage
- ✅ Exploratory testing completed (2 sessions)
- ✅ No P1 bugs found

**Performance Targets**:
- 100 items: <5 seconds total
- 500 items: <30 seconds total
- 10 concurrent operations: <10 seconds average

### Development Workflow Integration

**1. Pre-Commit Hook** (.husky/pre-commit):
```bash
#!/bin/sh
npm run test:unit  # Run unit tests
npm run lint       # Run linting
npm run format     # Run formatting
```

**2. CI Pipeline** (.github/workflows/test.yml):
```yaml
name: Test Suite
on: [pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run unit tests
        run: npm run test:unit
      - name: Run integration tests
        run: npm run test:integration
      - name: Run E2E tests (smoke)
        run: npm run test:e2e:smoke
      - name: Generate coverage report
        run: npm run test:coverage
      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v2
```

**3. PR Checklist Template**:
```markdown
## Testing Checklist

### Automated Tests
- [ ] All P0 tests implemented and passing
- [ ] Unit test coverage ≥80% for new code
- [ ] Integration tests cover all new endpoints
- [ ] E2E test covers happy path

### Manual Testing
- [ ] Functional test scenarios completed (5 scenarios)
- [ ] Edge cases verified (at least 8/12 edge cases tested)
- [ ] Exploratory testing completed (15 min session)

### Quality
- [ ] No P0 bugs found
- [ ] No P1 bugs found (or documented in issue tracker)
- [ ] Performance targets met (100 items <5s)

### Documentation
- [ ] Test plan added to PR description
- [ ] Known issues documented
- [ ] Manual test results summarized
```

**4. Definition of Done**:
- ✅ Feature implemented according to spec
- ✅ All P0 + P1 automated tests pass
- ✅ Manual testing checklist completed
- ✅ Code reviewed and approved
- ✅ No P0 bugs, P1 bugs documented
- ✅ Performance targets met
- ✅ Documentation updated
- ✅ Deployed to staging, smoke tested

### Monitoring & Maintenance

**Post-Launch**:
- Monitor error rates for bulk operations (target: <1% failure rate)
- Track performance metrics (P95 response time <10s)
- Watch for user-reported issues (bugs, confusion, frustration)
- Run weekly E2E test suite to catch regressions

**Test Maintenance**:
- Update tests when requirements change
- Add tests for newly discovered bugs (regression tests)
- Remove or update obsolete tests
- Keep test data fresh (use recent factories)

**Quarterly Review**:
- Analyze test coverage and identify gaps
- Review flaky tests and stabilize or remove
- Update success criteria based on user feedback
- Assess if performance targets still adequate
```

---

### Step 5: Documentation (2 min)

**Objective**: Create final test plan document ready to share

**Actions**:
1. **Consolidate Information**: Combine all outputs into single document
2. **Add Executive Summary**: 3-5 bullet point overview
3. **Format for Readability**: Use tables, checkboxes, clear headers
4. **Include Quick Reference**: 1-page summary for developers

**Output Format**:
```markdown
# Test Strategy: Bulk Operations Feature

**Feature**: Add bulk operations (select multiple items, perform actions)
**Date**: 2026-02-16
**Test Lead**: AI Specialist Agent

---

## Executive Summary

- **Test Coverage**: 26 automated tests + 12 manual scenarios designed
- **Priority Breakdown**: 6 P0 (critical), 18 P1 (high), 8 P2 (medium)
- **Estimated Effort**: 20 hours for P0+P1 tests (recommended scope)
- **Success Criteria**: 80%+ coverage, all P0 tests pass, no P0 bugs
- **Top Risks**: Permissions (security), transactions (data integrity), performance (scale)

---

## Quick Reference for Developers

### Must-Have Tests (P0) - Complete Before Merge
1. ✅ Permission validation (mixed permissions scenario)
2. ✅ Transaction rollback on error
3. ✅ API endpoint permission check
4. ✅ E2E happy path
5. ✅ E2E error scenario (permissions)
6. ✅ Partial failure handling

### Test Commands
```bash
# Run unit tests
npm run test:unit

# Run integration tests
npm run test:integration

# Run E2E tests
npm run test:e2e

# Run all tests + coverage
npm run test:all --coverage
```

### Definition of Done
- ✅ 6 P0 tests pass
- ✅ 80%+ unit test coverage
- ✅ Manual testing checklist complete
- ✅ No P0 bugs

---

## Full Test Plan

[Include all outputs from Step 1-4: Context Discovery, Test Gap Analysis, Test Strategy Design, Integration Recommendations]

---

## Appendix: Test Implementation Examples

[Include 2-3 full test implementations as examples]

---

**Questions?** Contact test lead or refer to full test strategy document.
```

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **Context discovered**: Read plan/task, analyzed existing tests, identified risk areas
- [ ] **Gaps identified**: Mapped components to tests, categorized gaps, prioritized by criticality
- [ ] **Tests designed**: Created unit, integration, E2E, manual, edge case, performance tests
- [ ] **Integration planned**: Defined test timing, implementation order, success criteria, workflow integration
- [ ] **Documented**: Consolidated into final test plan with executive summary and quick reference
- [ ] **Comprehensive**: Covers automated + manual, happy path + edge cases, functional + performance
- [ ] **Prioritized**: Clear P0/P1/P2 designation, MVP scope defined
- [ ] **Actionable**: Specific test names, inputs, expected outputs, commands to run

---

## Tips for Effective Test Strategy Design

1. **Start with risks**: Test critical paths (auth, payments, data integrity) first
2. **Balance coverage**: Mix unit (fast, many), integration (medium), E2E (slow, few)
3. **Think edge cases**: 0 items, 1 item, max items, errors, race conditions
4. **Make tests specific**: "Test bulk delete with mixed permissions" not "Test bulk delete"
5. **Define success upfront**: Coverage %, performance targets, bug tolerance
6. **Integrate with workflow**: Pre-commit hooks, CI pipeline, PR checklist
7. **Prioritize ruthlessly**: Not all tests are equal, focus on P0+P1 first
8. **Include manual testing**: Automated tests can't catch all issues (usability, UX, edge cases)
9. **Plan for maintenance**: Tests need updates as code changes, plan for it
10. **Make it easy to run**: Simple commands, fast feedback, clear pass/fail

---

## Integration with Other Skills

This skill works well with:

- **claude-instructions-optimization**: Ensure test strategies themselves are clear and concise
- **token-optimization-audit**: Test plans can be optimized for token efficiency
- **prompt-enhancement**: Improve test prompts for clarity and effectiveness

---

*Use this skill to add comprehensive test strategies to any implementation plan, ensuring quality and catching issues before production.*
