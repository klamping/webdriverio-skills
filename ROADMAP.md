# Roadmap

Planned skills and utilities for the WebdriverIO Skills project.

## Generic Skills

### WDIO Runner - Implemented
Runs WebdriverIO tests from the command line.

### Test Writer - Implemented
Writes clean, well-structured test code.

- Follows company code guidelines (ESLint, naming conventions, etc.)
- Understands Mocha syntax and page object patterns
- Creates "failure modes" to validate that assertions actually catch missing user actions
- Enforces selector rules (no flaky selectors, scoped to minimize conflicts)

### Skipped Test Manager - Implemented
Manages tests that need to be temporarily skipped.

- Skips tests for unimplemented functionality or app-level bugs using '.skip'
- Leaves a detailed comment in the code next to the skipped test, detailing when the test was skipped, root cause, etc.
- Links skipped tests to tickets in a ticketing system for tracking (if provided)
- Re-enables tests once the linked ticket is resolved (if provided and integrated)
- Provides a formatted report on skipped tests with details on how long the tests have been skipped for

### Test Flow Writer
Adds rich context to tests for improved reporting and traceability.

- Analyzes test suite names, page objects, and code actions
- Logs what each test was doing for better post-run analysis
- Retrofits context into existing tests to improve debugging

### Website Analyzer - Implemented

Investigates and documents site structure and functionality.

- Identifies key components (tab navigation, menus, tables, actions, etc.)
- Defines site structure for use by humans and agents
- Assigns importance levels to functionality (e.g., login = high, column sorting = lower)
- Compares versions of the site to surface differences (when available)

### Coverage Reporter

Correlates Website Analyzer output with the existing test suite.

- Maps features to tests
- Produces a coverage percentage showing how much functionality has correlated tests

### Project Customization Manager - Implemented

Each project has a lot of customizations. This skill is run upon fist use of these skills, in order to gather initial information about the project. It will scan the project directory, gathering information about the project. It will store information regarding the project in reference files, for use by the other skills, to help save on token usage and execution time. It can be run again on demand, when a user requests it, in order to gather the latest information after important code changes.  

Information to store:
- WDIO configuration(s)
- Reporters
- Services
- Coding standards & conventions
- Linting rules
- NPM scripts related to running tests
- Custom functionality (e.g. custom commands, API interfaces)
- Relevant environment variables (e.g., DEBUG=true to trigger 'debug' mode)
- Server information (e.g., local, dev, staging, prod)

It will also be run, if needed, at the end of orchestrator sessions, to update the project with any information that was changed during that session. This will be triggered by the orchestrator. 

We also need a way for teams to customize the skill to improve fit for their team. Possibly a 'custom-rules' reference? 

It also checks for functionality that improves skills abilities, such as:
- Using the JSON reporter for parsing test results
- Saving HTML/screenshots when a test fails (https://github.com/webdriverio/webdriverio/issues/2190#issuecomment-2245595191)

If that functionality is not found, it suggests adding it for the user. 

---

## Test Writing Skills

### Test Creation Manager
name: creating-new-tests

End-to-end coordinator for writing new tests from requirements.

- Intakes specs/requirements
- Uses Website Analyzer to understand current functionality
- Clarifies assumptions with the user before proceeding
- Delegates to Test Planner to organize the work
- Runs parallel Test Writer agents based on the plan
- Skips tests for functionality not yet implemented

### Test Planner
name: planning-tests

Creates a structured test plan from requirements.

- Defines data requirements for each test
- Generates test cases
- Links test cases to specific feature tickets

### Test Scaffolding - Implemented

Creates a scaffolded Mocha file 

### Plan Validator
Verifies that written tests match the test plan.

- Checks conformance of implemented tests against the plan
- Flags missing or misaligned test cases

---

## Failing Test Triage Skills

### Investigator - Implemented
The reasoning layer for diagnosing test failures.

- Does not write code or run tests directly
- Orchestrates other agents (context gathering, test runs, fixes)
- Analyzes failures in the context of recent code changes
- Prompts the user for confirmation or additional context
- Routes real app bugs to the Skipped Test Manager skill (to be implemented)

### Context Gatherer - Implemented
It reads artifacts to understand what a test was doing and where it broke.

- Reads test reports and logs
- Reads test files and related page objects
- Identifies the test flow and the likely point of failure

### REPL Runner

Knows how to run commands from the REPL for use in investigation and debugging.

### Improved Fixer
Implements the solution determined by the Investigator in a more skillful way

- Receives investigation summary and a specific task list
- Delegates implementation to the Test Writer
- Re-runs tests until they pass

### Improved Triage Reporter (may not be needed)
Produces a human-readable summary of what failed and what was done.

- Explains the root cause of the failure
- Documents the fix applied
- Improves long-term traceability of test history

### Large Run Evaluator
Processes large test run reports into an actionable failure list.

- Parses test run output
- Builds a structured list of failures for the Investigator