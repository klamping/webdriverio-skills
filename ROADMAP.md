# Roadmap

Planned skills and utilities for the WebdriverIO Skills project.

## Generic Skills

### WDIO Runner - DONE
Runs WebdriverIO tests from the command line.

### Test Writer
Writes clean, well-structured test code.

- Follows company code guidelines (ESLint, naming conventions, etc.)
- Understands Mocha syntax and page object patterns
- Creates "failure modes" to validate that assertions actually catch missing user actions
- Enforces selector rules (no flaky selectors, scoped to minimize conflicts)

### Skipped Test Manager
Manages tests that need to be temporarily skipped.

- Skips tests for unimplemented functionality or app-level bugs
- Links skipped tests to tickets in a ticketing system for tracking
- Re-enables tests once the linked ticket is resolved

### Test Context Writer
Adds rich context to tests for improved reporting and traceability.

- Analyzes test suite names, page objects, and code actions
- Logs what each test was doing for better post-run analysis
- Retrofits context into existing tests to improve debugging

### Website Analyzer
Investigates and documents site structure and functionality.

- Identifies key components (tab navigation, menus, tables, actions, etc.)
- Defines site structure for use by humans and agents
- Assigns importance levels to functionality (e.g., login = high, column sorting = lower)
- Compares versions of the site to surface differences (when available)

### Coverage Reporter _(stretch goal)_
Correlates Website Analyzer output with the existing test suite.

- Maps features to tests
- Produces a coverage percentage showing how much functionality has correlated tests

---

## Test Writing Skills

### Orchestrator
End-to-end coordinator for writing new tests from requirements.

- Intakes specs/requirements
- Uses Website Analyzer to understand current functionality
- Clarifies assumptions with the user before proceeding
- Delegates to Test Planner to organize the work
- Runs parallel Test Writer agents based on the plan
- Skips tests for functionality not yet implemented

### Test Planner
Creates a structured test plan from requirements.

- Defines data requirements for each test
- Generates test cases
- Links test cases to specific feature tickets

### Plan Validator
Verifies that written tests match the test plan.

- Checks conformance of implemented tests against the plan
- Flags missing or misaligned test cases

---

## Failing Test Triage Skills

### Investigator
The reasoning layer for diagnosing test failures.

- Does not write code or run tests directly
- Orchestrates other agents (context gathering, test runs, fixes)
- Analyzes failures in the context of recent code changes
- Prompts the user for confirmation or additional context
- Routes real app bugs to the Skipped Test Manager

### Context Gatherer - DONE
It reads artifacts to understand what a test was doing and where it broke.

- Reads test reports and logs
- Reads test files and related page objects
- Identifies the test flow and the likely point of failure

### REPL Runner

Knows how to run commands from the REPL for use in investigation and debugging.

### Fixer
Implements the solution determined by the Investigator.

- Receives investigation summary and a specific task list
- Delegates implementation to the Test Writer
- Re-runs tests until they pass

### Triage Reporter
Produces a human-readable summary of what failed and what was done.

- Explains the root cause of the failure
- Documents the fix applied
- Improves long-term traceability of test history

### Large Run Evaluator
Processes large test run reports into an actionable failure list.

- Parses test run output
- Builds a structured list of failures for the Investigator