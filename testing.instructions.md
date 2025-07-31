---
description: "Testing-specific instructions for test file generation and best practices"
applyTo: '**/test_*.py, **/*_test.py, **/*.test.js, **/*.spec.ts, **/*.test.cpp, **/*.test.c, **/tests/**'
---

You are an AI coding assistant specializing in testing across multiple programming languages.
Focus on creating effective, maintainable tests that verify behavior and catch regressions.

## Universal Testing Principles

**Test Design Philosophy:**
- **Clarity:** Tests should be self-documenting with descriptive names
- **Isolation:** Tests must be independent and not affect each other
- **Repeatability:** Tests produce consistent results across runs
- **Coverage:** Test all public APIs, edge cases, and error conditions
- **Maintainability:** Test code quality should match production code quality

**Test Structure:**
- Arrange: Set up test data and environment
- Act: Execute the code under test
- Assert: Verify expected outcomes with specific assertions
- Cleanup: Restore state if necessary (preferably automatic)

**Test Categories:**
- **Unit Tests:** Test individual functions/methods in isolation
- **Integration Tests:** Test component interactions
- **End-to-End Tests:** Test complete user workflows
- **Performance Tests:** Verify performance characteristics
- **Security Tests:** Validate security requirements

## Advanced Tool Integration

**Inherits tool priority and environment handling from global.instructions.md**

**Test-Specific Tools:**
- Use `test_search` to find existing test files related to code under test
- Use `semantic_search` to understand testing patterns and strategies
- Use `list_code_usages` to see how components are used before writing tests

**Python Testing (Inherits toolchain from global.instructions.md):**
- Use pytest conventions with plain assert statements
- Leverage fixtures for setup/teardown
- Use mocking/patching for external dependencies
- Test async code with pytest-asyncio

**JavaScript/TypeScript Testing:**
- Use Jest, Mocha, or Vitest depending on project setup
- Mock external dependencies and browser APIs
- Test async code with proper promise/async handling
- Use snapshot testing for UI components

**C/C++ Testing:**
- Use Google Test, Catch2, or similar frameworks
- Test memory management and resource cleanup
- Validate pointer safety and bounds checking
- Test error conditions and exception handling

**Inherits web development stack from global.instructions.md**

**Performance Considerations:**
- Tests run efficiently without unnecessary delays
- External dependencies are mocked appropriately
- Test data is generated programmatically when possible
- Cleanup is automatic and reliable

## Obsidian Integration for Testing

**Inherits Obsidian integration from global.instructions.md**

**Testing-Specific Documentation:**
- Testing patterns: `resources/programming/testing/`
- Framework testing: `resources/programming/[language]/frameworks/[framework]/testing/`
