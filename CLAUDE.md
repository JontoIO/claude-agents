# Claude Code Instructions — claude-agents Marketplace

## Plugin Versioning (REQUIRED)

**Whenever you modify any file inside a plugin directory, you MUST:**

1. **Bump the version** in `plugins/<plugin-name>/.claude-plugin/plugin.json`
2. **Add a changelog entry** in `plugins/<plugin-name>/CHANGELOG.md`
3. **Update the version** referenced in `README.md` if it appears there

### Versioning Rules (Semantic Versioning)

| Change type | Version bump | Examples |
|---|---|---|
| New skill, new command, new agent | **minor** (1.0.0 → 1.1.0) | Adding `user-story-discovery` skill |
| Bug fix, wording correction, minor improvement | **patch** (1.0.0 → 1.0.1) | Fixing a typo in a skill, correcting a step |
| Breaking change to agent interface or skill API | **major** (1.0.0 → 2.0.0) | Renaming commands, restructuring skill steps |

### CHANGELOG Entry Format

Follow [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) format:

```markdown
## [1.1.0] - YYYY-MM-DD

### ✨ Added
- New skill: `skill-name` — one-line description

### 🔧 Changed
- Updated `file` — what changed and why

### 🐛 Fixed
- Fixed `file` — what was wrong
```

### What counts as a plugin modification

- Any file under `plugins/<name>/skills/`
- Any file under `plugins/<name>/commands/`
- Any file under `plugins/<name>/agents/`
- Any file under `plugins/<name>/examples/`
- The plugin's `README.md`

Changes to the root `README.md` or `CLAUDE.md` do **not** require a plugin version bump.

---

## README Sync (REQUIRED)

Whenever you add or modify a plugin's skills, commands, or capabilities, also update the root `README.md`:

- Skills list and count in the plugin's **Components** section
- Commands list and count in the plugin's **Components** section
- Directory tree counts (e.g., `# 6 product skills`)
- Plugin description if capabilities changed significantly

---

## Repository Structure

```
claude-agents/
├── CLAUDE.md                        # This file
├── README.md                        # Marketplace overview (keep in sync)
├── .claude-plugin/
│   └── marketplace.json
└── plugins/
    └── <plugin-name>/
        ├── .claude-plugin/
        │   └── plugin.json          # ← bump version here on every change
        ├── agents/
        ├── skills/
        ├── commands/
        ├── examples/
        ├── README.md
        └── CHANGELOG.md             # ← add entry here on every change
```

## Current Plugins

| Plugin | Current Version |
|---|---|
| `financial-advisor` | 1.0.0 |
| `product-manager` | 1.1.0 |
| `ai-specialist` | 1.0.0 |
| `tax-advisor` | 1.0.0 |
| `ceo` | 1.0.0 |
| `qa-engineer` | 1.0.0 |
