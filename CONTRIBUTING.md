# Contributing to Claude Agents Marketplace

Thank you for your interest in contributing to the Claude Agents Marketplace! This document provides guidelines for contributing plugins, improving existing plugins, and maintaining the marketplace.

## 📋 How to Contribute

### 1. Fork and Clone

1. Fork this repository
2. Clone your fork locally
3. Create a new branch for your contribution

```bash
git clone https://github.com/YOUR_USERNAME/claude-agents.git
cd claude-agents
git checkout -b your-feature-branch
```

### 2. Choose What to Contribute

You can contribute in several ways:

- **New Plugins**: Complete plugin packages with agents, skills, and commands
- **Plugin Improvements**: Enhancements to existing plugins
- **Documentation**: Guides, examples, and tutorials
- **Bug Fixes**: Fix issues in existing plugins or infrastructure

## 🔌 Creating a New Plugin

### Plugin Structure

Every plugin must follow this structure:

```
plugins/
└── your-plugin-name/
    ├── .claude-plugin/
    │   └── plugin.json              # Plugin manifest (REQUIRED)
    ├── agents/
    │   └── agent-name.md            # Agent definitions
    ├── skills/
    │   └── skill-name/
    │       └── SKILL.md             # Skill definitions
    ├── commands/
    │   └── command-name.md          # Command definitions
    ├── examples/
    │   └── example-name.md          # Usage examples
    ├── README.md                    # Plugin documentation (REQUIRED)
    └── CHANGELOG.md                 # Version history (REQUIRED)
```

### Plugin Manifest (plugin.json)

Create `.claude-plugin/plugin.json` with the following structure:

```json
{
  "name": "your-plugin-name",
  "description": "Brief description of your plugin",
  "version": "1.0.0",
  "author": {
    "name": "Your Name",
    "email": "your@email.com"
  },
  "homepage": "https://github.com/yourusername/claude-agents",
  "repository": "https://github.com/yourusername/claude-agents",
  "license": "MIT",
  "keywords": [
    "keyword1",
    "keyword2",
    "keyword3"
  ]
}
```

### Agent Files (agents/*.md)

Agent files use markdown with YAML frontmatter:

```markdown
---
name: agent-name
description: Brief description of what this agent does and when to use it.
---

You are a [agent role]. Your expertise covers:

## Capabilities
- Capability 1
- Capability 2

## Approach
1. Step 1
2. Step 2

[Detailed instructions for the agent...]
```

### Skill Files (skills/*/SKILL.md)

Skill files use markdown with YAML frontmatter:

```markdown
---
name: skill-name
description: Brief description of what this skill does and when to use it.
---

You are a [skill specialist]. Follow this approach:

## Step 1: [Step Name]
[Detailed instructions...]

## Step 2: [Step Name]
[Detailed instructions...]

[Complete skill instructions...]
```

### Command Files (commands/*.md)

Command files are markdown documents with instructions:

```markdown
# Command Name

Brief description of what this command does.

## Purpose
- Use case 1
- Use case 2

## Usage
\`\`\`bash
/plugin-name:command-name [arguments]
\`\`\`

[Detailed command documentation...]
```

### Plugin README.md

Every plugin must have a comprehensive README.md:

```markdown
# Plugin Name

Brief description of the plugin.

## Overview
Detailed overview of what the plugin does and who it's for.

## Features
- Feature 1
- Feature 2

## Installation
\`\`\`bash
/plugin install your-plugin-name@jontoio-claude-agents
\`\`\`

## Usage
[Usage examples for agents, skills, and commands]

## Components
### Agent: agent-name
[Description]

### Skills
- \`skill-name\`: [Description]

### Commands
- \`command-name\`: [Description]

## Examples
[Practical examples]

## Version History
See [CHANGELOG.md](./CHANGELOG.md)

## License
MIT
```

### Plugin CHANGELOG.md

Track version history in CHANGELOG.md:

```markdown
# Changelog

## [1.0.0] - YYYY-MM-DD
### Added
- Initial release
- Feature 1
- Feature 2

### Changed
- N/A

### Fixed
- N/A
```

## ✅ Quality Standards

### Documentation Requirements

- **Clear Purpose**: Explain what the plugin does and when to use it
- **Usage Examples**: Provide practical, real-world examples
- **Complete Instructions**: Agents and skills must have detailed step-by-step instructions
- **Dependencies**: List any required tools, MCP servers, or resources
- **Limitations**: Document known limitations or constraints

### Naming Conventions

- **Plugins**: `lowercase-with-hyphens` (e.g., `financial-advisor`, `code-reviewer`)
- **Agents**: `lowercase-with-hyphens` (e.g., `financial-advisor`, `security-auditor`)
- **Skills**: `lowercase-with-hyphens` (e.g., `cost-estimation`, `vulnerability-scanning`)
- **Commands**: `lowercase-with-hyphens` (e.g., `quick-cost-estimate`, `review-pr`)

### Testing Requirements

Before submitting a plugin:

1. **Local Testing**: Test your plugin locally
   ```bash
   # Add marketplace locally
   /plugin marketplace add ./

   # Install your plugin
   /plugin install your-plugin-name@jontoio-claude-agents

   # Test all components
   /your-plugin-name:command-name
   /agents  # Verify agent appears
   ```

2. **Component Testing**: Verify each component works
   - Test all skills can be invoked
   - Test all commands execute correctly
   - Test agent appears in `/agents` list
   - Test examples in README work as documented

3. **Documentation Testing**: Verify documentation is accurate
   - All links work
   - Code examples are correct
   - Installation instructions are accurate

## 🚀 Submission Process

### Adding Your Plugin to the Marketplace

1. **Create Plugin Directory**: Add your plugin to `plugins/your-plugin-name/`

2. **Update Marketplace Manifest**: Add your plugin to `.claude-plugin/marketplace.json`:

```json
{
  "plugins": [
    {
      "name": "your-plugin-name",
      "source": "./plugins/your-plugin-name",
      "description": "Brief description",
      "version": "1.0.0",
      "author": {
        "name": "Your Name"
      },
      "keywords": ["keyword1", "keyword2"]
    }
  ]
}
```

3. **Update Root README**: Add your plugin to the "Available Plugins" section

4. **Submit Pull Request**:
   - Clear PR title: "Add [plugin-name] plugin"
   - Description explaining what the plugin does
   - Link to any relevant issues
   - Screenshots or examples if applicable

### Pull Request Checklist

- [ ] Plugin follows required directory structure
- [ ] `plugin.json` manifest is valid JSON
- [ ] All required files present (README.md, CHANGELOG.md)
- [ ] Agents have proper YAML frontmatter
- [ ] Skills have proper YAML frontmatter
- [ ] Commands are well-documented
- [ ] Plugin tested locally and works
- [ ] Documentation is complete and accurate
- [ ] Marketplace manifest updated
- [ ] Root README updated
- [ ] No sensitive or personal information included
- [ ] Code of Conduct followed

## 🔄 Improving Existing Plugins

### Enhancement Process

1. **Open an Issue**: Describe the improvement you want to make
2. **Get Feedback**: Discuss with maintainers before major changes
3. **Make Changes**: Follow existing plugin structure and conventions
4. **Update Version**: Bump version in `plugin.json` and `marketplace.json`
5. **Update CHANGELOG**: Document changes in plugin's CHANGELOG.md
6. **Submit PR**: Reference the original issue

### Bug Fixes

1. **Report Bug**: Open an issue describing the bug
2. **Fix Bug**: Make minimal changes to fix the issue
3. **Test Fix**: Verify the bug is resolved
4. **Update CHANGELOG**: Document the fix
5. **Submit PR**: Reference the bug issue

## 🚫 What Not to Include

- Personal or sensitive information (API keys, credentials)
- Copyrighted content without permission
- Malicious or harmful code/prompts
- Overly specific or single-use configurations
- Plugins without clear use cases or value
- Incomplete or poorly documented plugins

## 📝 Code of Conduct

Please be respectful and constructive in all interactions:

- Be welcoming to newcomers
- Be respectful of differing viewpoints
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

## 💡 Need Help?

- **Questions**: Open an issue with the "question" label
- **Examples**: Check the `financial-advisor` plugin as a reference
- **Guidance**: Reach out to maintainers via issues
- **Documentation**: See [Plugin Development Guide](./docs/creating-plugins.md)

## 🔍 Review Process

Pull requests will be reviewed for:

1. **Quality**: Plugin provides clear value and is well-implemented
2. **Documentation**: Complete, accurate, and well-written documentation
3. **Standards**: Follows structure, naming, and testing requirements
4. **Compatibility**: No conflicts with existing plugins
5. **Maintenance**: Author willing to maintain the plugin

Reviews typically take 3-7 days. Be patient and responsive to feedback.

## 📊 Plugin Versioning

Follow [Semantic Versioning](https://semver.org/):

- **MAJOR** (1.0.0 → 2.0.0): Breaking changes
- **MINOR** (1.0.0 → 1.1.0): New features, backwards-compatible
- **PATCH** (1.0.0 → 1.0.1): Bug fixes, backwards-compatible

When updating a plugin:
1. Bump version in `plugin.json`
2. Bump version in `.claude-plugin/marketplace.json`
3. Update CHANGELOG.md with changes
4. Update README.md if needed

## 🎯 Plugin Ideas

Looking for ideas? Consider creating plugins for:

- **Development**: Code review, refactoring, testing
- **Documentation**: API docs, README generation, tutorials
- **Security**: Vulnerability scanning, security audits
- **Project Management**: Sprint planning, estimation, roadmapping
- **Design**: UI/UX review, accessibility audits
- **Data Analysis**: Data visualization, statistical analysis
- **DevOps**: CI/CD optimization, infrastructure analysis

## 🙏 Recognition

Contributors will be recognized in:
- Plugin README (for plugin-specific contributions)
- Marketplace README (for significant contributions)
- Release notes

Thank you for contributing to the Claude Agents Marketplace! Together we're building a valuable collection of tools for the Claude community.
