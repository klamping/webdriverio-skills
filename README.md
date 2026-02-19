# WebdriverIO Skills

A collection of agent skills for running, creating, and triaging [WebdriverIO](https://webdriver.io/) tests. These skills work with any AI coding agent that supports the open agent skills standard, including OpenCode, Claude Code, Cursor, Codex, and [many others](https://github.com/vercel-labs/skills#available-agents).

See [ROADMAP.md](./ROADMAP.md) for planned skills.

## Available Skills

| Skill | Description |
|---|---|
| `running-webdriverio-tests` | Run WebdriverIO test files from the command line. Use when debugging tests, gathering context about test behavior, or verifying changes resolved an issue. |
| `context-gatherer` | Reads test artifacts to understand what a failing test was doing and where it broke. Part of the failing test triage pipeline — called by the Investigator agent. |

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
