# WebdriverIO Skills

A collection of agent skills for running, creating, and triaging [WebdriverIO](https://webdriver.io/) tests. These skills work with any AI coding agent that supports the open agent skills standard, including OpenCode, Claude Code, Cursor, Codex, and [many others](https://github.com/vercel-labs/skills#available-agents).

See [ROADMAP.md](./ROADMAP.md) for planned skills.

## Available Skills

| Skill | Description |
|---|---|
| `running-webdriverio-tests` | Run WebdriverIO test files from the command line. Use when debugging tests, gathering context about test behavior, or verifying changes resolved an issue. |
| `gathering-context` | Reads test artifacts to understand what a failing test was doing and where it broke. Part of the failing test triage pipeline and called by the Investigator agent. |
| `creating-test-structure` | Create or extend WebdriverIO test scaffolding from a markdown test plan using `describe` / `it` / hooks and pseudo-code comments. |
| `writing-webdriverio-code` | Implement, extend, or fix WebdriverIO tests by converting pseudo-code scaffolds or editing existing specs with maintainable WDIO commands and assertions. |
| `managing-project-customizations` | Initialize and refresh project-specific WebdriverIO context caches (configs, conventions, scripts, env targets, and recommendations) for faster downstream skill execution. |
| `investigate-failing-tests` | Orchestrate failing test diagnosis and fix loops by delegating context gathering, test execution, and implementation to other skills with bounded retry guardrails. |
| `skipped-test-manager` | Manage temporary `.skip` usage for app bugs or unimplemented functionality with metadata, ticket linkage, re-enable workflow, and aging reports. |
| `analyze-website` | Investigate and document site structure, component inventory, functionality importance, and version-to-version differences for test planning and impact analysis. |

## Installation

Install skills using the [`npx skills`](https://github.com/vercel-labs/skills) CLI.

### Install all skills

```bash
npx skills add klamping/webdriverio-skills
```

### Install a specific skill

```bash
npx skills add klamping/webdriverio-skills --skill running-webdriverio-tests
```

### Install globally (user-level, available in all projects)

```bash
npx skills add klamping/webdriverio-skills -g
```
