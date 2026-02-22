# Changelog

All notable changes to the QA Engineer plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-22

### Added
- Initial release of QA Engineer plugin
- QA engineer agent with evidence-first, confirm-before-persisting design philosophy
- Happy path mapping skill with 5-step discovery-to-documentation framework
- Bug hunt skill covering 4 detection categories: console errors, broken pages, broken endpoints, unexpected UX behavior
- Regression testing skill with pass/fail dashboard, BUG-XXX auto-generation, and release recommendation
- Quick health check command for 5-minute traffic-light app snapshots
- Suggest happy paths command with multi-source analysis (git log, bug reports, coverage gaps)
- Comprehensive documentation and e-commerce checkout example

### Features
- HP-XXX numbered happy path files with YAML frontmatter (id, status, priority, tags)
- BUG-XXX structured bug reports with severity, evidence, impact, and suggested fix direction
- Happy-path/ folder created in target project (not plugin) for version-controlled QA documentation
- AskUserQuestion confirmation required before any file is written to disk
- Priority system: P0 (revenue/auth) → P1 (core) → P2 (supporting) → P3 (edge/admin)
- Traffic light status indicators: 🟢 healthy, 🟡 degraded, 🔴 critical
- INDEX.md auto-generated to list all HP files with status table

### Skills
- `happy-path-mapping`: 5-step flow discovery, prioritization, HP file generation, folder setup, and summary
- `bug-hunt`: 4-category detection with grep patterns, curl commands, and severity assignment criteria
- `regression-testing`: HP inventory, step-by-step execution, report generation, post-regression actions

### Commands
- `quick-health-check`: Rapid 5-check health snapshot in under 5 minutes
- `suggest-happy-paths`: Multi-source HP candidate analysis with `--from-bug`, `--recent-changes`, `--coverage-gaps` flags

### Agent
- `qa-engineer`: Methodical specialist with defined tool usage, integration with CEO/PM/ai-specialist, and clear limitations

### Documentation
- Full README with usage walkthrough, HP file structure, BUG report structure
- E-commerce checkout example covering all 3 skills in a realistic scenario
- SKILL.md files for each skill with step-by-step frameworks, templates, and tips

### Examples
- `ecommerce-checkout-qa.md`: Next.js e-commerce platform — maps 7 flows, hunts 4 bugs (including P0 security issue), runs post-fix regression

### Integration
- CEO agent updated to detect qa-engineer and delegate quality/testing questions
- marketplace.json updated with qa-engineer entry and keywords

### Design Decisions
- HP files live in the target project (`happy-path/`), not in the plugin — QA documentation belongs with the code it tests
- All file creation requires user confirmation — no silent side effects
- YAML frontmatter on all HP and BUG files — enables future tooling to parse and query QA artifacts
- Bug reports generated automatically during regression — no manual reporting step
- `status: draft` default for all generated HPs — human review required before marking active

### Known Limitations
- Cannot execute browser JavaScript — SPA rendering and click interactions require manual verification
- Authenticated endpoint testing requires the user to supply a token or cookie
- Static analysis for console errors may produce false positives (pattern matches that aren't real bugs)
- HP files document intent; actual pass/fail depends on the target environment being reachable

### Future Roadmap
- Integration with GitHub Issues for automatic BUG-XXX → issue creation
- Playwright/Cypress script generation from active HP files
- Scheduled regression runs via hooks
- HP coverage dashboard with trend tracking across regression runs
- Support for OpenAPI spec import to auto-generate HP files for all documented endpoints

## How to Upgrade

Check your current version:
```bash
cat plugins/qa-engineer/.claude-plugin/plugin.json | grep version
```

Update to latest:
```bash
/plugin update qa-engineer@jontoio-claude-agents
```

## Support

- GitHub Issues: https://github.com/jontoIO/claude-agents/issues
- Documentation: https://github.com/jontoIO/claude-agents/tree/main/plugins/qa-engineer

**Note**: This plugin follows semantic versioning. Patch releases fix bugs in the plugin itself. Minor releases add new detection patterns or HP template improvements. Major releases change the HP file format or folder structure (which would require migrating existing happy-path/ files).
