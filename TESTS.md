# Testing Standards

## Test Execution Requirements

**MANDATORY**: ALL unit tests, integration tests, and end-to-end tests MUST pass before any production readiness claims.

### Test Suite Status
- **100% pass rate** on all unit, integration, and end-to-end tests is MANDATORY
- Test execution results must be verified and documented
- No production readiness claims without explicit test confirmation

## Unit Testing Standards

### Code Quality Metrics
- **Line Coverage**: Target 70-80% code coverage for all business logic (diminishing returns beyond this)
- **Branch Coverage**: Target 70%+, ideally 80-90% (ensures all decision paths are tested)
- **Code Complexity**: Cyclomatic Complexity must be <10 per function/method (ideal range 1-5)
- **CRAP Score**: Change Risk Anti-Patterns (CRAP) score must be <15 per method (<10 is excellent)
  - Formula: `CRAP = CC² × (1 - Coverage%)³ + CC`
  - CRAP > 30 is considered dangerous and requires immediate refactoring

### Test Quality Requirements
Each function/method must have tests for:
- Happy path scenarios
- Error conditions and edge cases
- Input validation and boundary conditions
- Null/undefined/empty value handling

### Test Implementation Standards
- **Test Isolation**: Tests must be independent and not rely on external dependencies
- **Mock Usage**: External services, databases, and APIs must be properly mocked

## Integration Testing Standards

### API Testing Requirements
- **API Endpoint Coverage**: ≥ 90% of public REST/GraphQL endpoints tested
- **Input Validation**: Typical scenarios + edge cases + boundary conditions tested
- **Response Validation**: Status codes + schema validation for all endpoints
- **Authentication Coverage**: All auth paths (login/refresh/expiry) + RBAC for all endpoints

### Database Testing Requirements
- **Database Operations**: All major CRUD operations tested with real database connections
- **Referential Integrity**: Database constraints and relationships validated
- **Data Rollback**: 100% test cleanup with proper rollback on failures

### Service Integration Requirements
- **Service Communication**: All downstream service calls tested (with appropriate mocking)
- **Error Handling**: Network failures, timeouts, and 3rd party service downtime scenarios
- **Performance**: P99 response time ≤ 500ms per endpoint (adjust based on SLA)
- **Test Suite Duration**: ≤ 5 minutes for full integration test suite
- **Integration Test Coverage**: 60-80% code coverage from integration tests alone

## End-to-End Testing Standards (Playwright)

### Framework Requirements
- **Framework**: Use Playwright for all E2E testing with Playwright MCP integration
- **Test Pass Rate**: ≥ 95% for stable releases; 100% in protected branches
- **Flaky Test Rate**: < 2% (flaky = sometimes pass/fail with no code change)
- **Test Duration**: ≤ 30 seconds per test; total suite ≤ 5-10 minutes
- **Retry Usage**: < 5% of tests requiring retries (> 10% indicates environment instability)

### Coverage and Organization
- **Test Coverage**: ≥ 80% line/branch coverage combining unit and E2E coverage
- **Test Organization**: Proper tagging with `@smoke`, `@critical`, `@a11y`, `@regression`
- **User Journey Coverage**: All documented user flows must have corresponding E2E tests

### Technical Requirements
- **Cross-browser Testing**: Tests run on Chromium, Firefox, and WebKit
- **Performance Monitoring**: Track page load times, Core Web Vitals, and network requests
- **Visual Regression**: Screenshot comparisons for UI consistency
- **Accessibility**: Automated a11y testing with axe-playwright integration
- **Test Isolation**: Each test runs in isolated browser context with proper cleanup

## Test Environment Requirements

### Infrastructure Standards
- **Test Data**: Proper test fixtures and seed data for consistent testing
- **Environment Isolation**: Tests run in isolated environments without affecting production
- **CI/CD Integration**: All tests must pass in continuous integration pipeline
- **Playwright Configuration**: Proper playwright.config.js with browser matrix and retry logic
- **Test Reporting**: Clear test results with failure details, coverage reports, and Playwright HTML reports
- **Parallel Execution**: Tests can run concurrently without conflicts
- **Playwright MCP**: Leverage Playwright MCP for enhanced test automation and debugging capabilities

## Quality Metrics Summary

### Code Quality Metrics

| Metric | Good Threshold | Red Flag | Action Required |
|--------|---------------|----------|-----------------|
| **Line Coverage** | 70-80% | < 50% | Increase test coverage |
| **Branch Coverage** | 80-90% | < 60% | Focus on logic-heavy classes |
| **Cyclomatic Complexity** | < 10 | > 15 | Refactor large methods |
| **CRAP Score** | < 15 (< 10 excellent) | > 30 | Immediate refactoring required |

### E2E Quality Metrics (Playwright)

| Metric | Target | Tolerance | Red Flag |
|--------|--------|-----------|----------|
| **Test Pass Rate** | ≥ 95% | 90-94% | < 90% 🚨 |
| **Flaky Test Rate** | ≤ 2% | 2-5% | > 5% 🔥 |
| **Avg Test Duration** | ≤ 30s per test | 30-120s | > 2 min 🐢 |
| **E2E Coverage** | ≥ 80% | 70-79% | < 70% ⚠️ |
| **Retry Usage** | < 5% | 5-10% | > 10% (unstable) |

### Integration Test Quality Metrics

| Metric | Target | Tolerance | Red Flag |
|--------|--------|-----------|----------|
| **API Endpoint Coverage** | ≥ 90% | 80-89% | < 80% 🚨 |
| **Test Pass Rate** | 95-100% | 90-94% | < 90% 🚨 |
| **Test Flakiness** | < 2% | 2-5% | > 5% 🔥 |
| **P99 Response Time** | ≤ 500ms | 500-1000ms | > 1s 🐢 |
| **Suite Duration** | ≤ 5 min | 5-10 min | > 10 min ⏰ |
| **Integration Coverage** | 60-80% | 50-59% | < 50% ⚠️ |
| **Retry Rate** | < 5% | 5-10% | > 10% (unstable) |

## Key Testing Principles

- High branch coverage with meaningful assertions > high line coverage with weak tests
- CRAP score combines complexity and coverage to identify truly risky code
- Methods with Cyclomatic Complexity > 15 should be broken into smaller functions
- Focus testing efforts on business-critical and complex logic rather than chasing 100% coverage
- Flaky tests indicate environmental issues or race conditions that must be resolved
- E2E tests should use proper tagging (@smoke, @critical, @a11y, @regression) for targeted testing
- Integration tests must use real databases/services, not mocks, for true integration validation
- API contract testing ensures proper request/response handling and schema compliance
- Performance thresholds must align with defined SLAs and user experience requirements

## Communication Guidelines

### NEVER claim production readiness without:
- Explicit confirmation that ALL tests (unit/integration/e2e) are passing
- Evidence of test execution results
- Verification of test coverage adequacy
- Confirmation that quality metrics meet defined thresholds

### Instead of saying "production ready," use specific language:
- "Ready for staging deployment with [specific caveats]"
- "Requires [specific improvements] before production use"
- "MVP implementation - needs [security/performance/testing] hardening"
- "Functional but requires production-grade [error handling/monitoring/etc.]"
- "Tests passing but needs [specific area] verification before production"

## Implementation Checklist

### Pre-Production Testing Requirements
- [ ] All unit tests passing with 100% pass rate
- [ ] All integration tests passing with 100% pass rate
- [ ] All end-to-end tests passing with 100% pass rate
- [ ] Test execution results documented and verified
- [ ] No failing tests in CI/CD pipeline

### Unit Test Quality Gates
- [ ] Line coverage: 70-80% achieved for business logic
- [ ] Branch coverage: 80-90% achieved for critical paths
- [ ] Cyclomatic complexity: <10 per function/method
- [ ] CRAP score: <15 per method (<10 preferred)
- [ ] All functions have tests for happy path, error conditions, edge cases
- [ ] External dependencies properly mocked
- [ ] Tests are isolated and independent

### Integration Test Validation
- [ ] API endpoint coverage: ≥90% of public endpoints tested
- [ ] All CRUD operations tested with real database connections
- [ ] Authentication and authorization paths tested
- [ ] Error handling scenarios tested (network failures, timeouts)
- [ ] P99 response time ≤500ms per endpoint
- [ ] Integration test suite completes in ≤5 minutes
- [ ] Integration test coverage: 60-80% achieved

### End-to-End Test Completion (Playwright)
- [ ] Test pass rate: ≥95% for stable releases (100% for protected branches)
- [ ] Flaky test rate: <2%
- [ ] Average test duration: ≤30 seconds per test
- [ ] Total suite duration: ≤5-10 minutes
- [ ] Retry usage: <5% of tests
- [ ] Cross-browser testing completed (Chromium, Firefox, WebKit)
- [ ] All user journeys have corresponding E2E tests
- [ ] Tests properly tagged (@smoke, @critical, @a11y, @regression)
- [ ] Visual regression testing completed
- [ ] Performance monitoring implemented
- [ ] Accessibility testing with axe-playwright completed

### Test Environment Verification
- [ ] Test data and fixtures properly configured
- [ ] Environment isolation verified
- [ ] Playwright configuration (playwright.config.js) properly set up
- [ ] Test reporting configured (HTML reports, coverage reports)
- [ ] Parallel execution working without conflicts
- [ ] Playwright MCP integration functional

### Quality Metrics Validation
- [ ] All quality metrics meet defined thresholds
- [ ] No red flag indicators present
- [ ] Quality gate reviews completed
- [ ] Test coverage reports generated and reviewed
- [ ] Performance benchmarks documented

### Documentation and Communication
- [ ] Test results documented with evidence
- [ ] Any test limitations or caveats clearly stated
- [ ] Specific language used (no premature "production ready" claims)
- [ ] Test coverage gaps identified and documented
- [ ] Next steps for production readiness clearly outlined