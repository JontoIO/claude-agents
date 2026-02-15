# Creating Plugins for Claude Agents Marketplace

This guide walks you through creating a new plugin for the Claude Agents Marketplace.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Plugin Structure](#plugin-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Testing Your Plugin](#testing-your-plugin)
- [Publishing Your Plugin](#publishing-your-plugin)
- [Best Practices](#best-practices)

## Overview

A Claude plugin is a self-contained package that extends Claude's capabilities with:
- **Agents**: Specialized personas with specific knowledge domains
- **Skills**: Structured methodologies for accomplishing tasks
- **Commands**: Quick actions for common operations

Plugins are installed via the Claude Code plugin system and namespaced to avoid conflicts.

## Prerequisites

Before creating a plugin, you should have:

1. **Claude Code** installed and working
2. **Familiarity with Claude**: Understand how to write effective prompts
3. **Domain Expertise**: Deep knowledge of the area your plugin will cover
4. **Git**: Basic Git knowledge for version control
5. **Markdown**: Comfortable writing documentation in Markdown

## Plugin Structure

Every plugin follows this structure:

```
plugins/your-plugin-name/
├── .claude-plugin/
│   └── plugin.json              # Plugin metadata (REQUIRED)
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

### File Formats

**Plugin Manifest** (`plugin.json`):
- JSON format
- Contains metadata about the plugin
- Defines version, author, keywords

**Agent Files** (`.md` with YAML frontmatter):
- Define agent persona and capabilities
- Include detailed instructions for the agent

**Skill Files** (`SKILL.md` with YAML frontmatter):
- Define structured methodologies
- Step-by-step instructions for accomplishing tasks

**Command Files** (`.md`):
- Quick reference for specific operations
- Usage examples and parameters

## Step-by-Step Guide

### Step 1: Plan Your Plugin

Before writing code, answer these questions:

1. **What problem does it solve?**
   - Be specific about the use case
   - Example: "Helps developers estimate project costs accurately"

2. **Who is the target user?**
   - Define your audience
   - Example: "Startup founders, product managers, CTOs"

3. **What components do you need?**
   - Agent: Yes/No (do you need a persistent persona?)
   - Skills: How many? What methodologies?
   - Commands: What quick actions make sense?

4. **What makes it unique?**
   - Why is this better than asking Claude directly?
   - What structure or methodology does it provide?

### Step 2: Create the Directory Structure

```bash
cd claude-agents
mkdir -p plugins/your-plugin-name/.claude-plugin
mkdir -p plugins/your-plugin-name/agents
mkdir -p plugins/your-plugin-name/skills
mkdir -p plugins/your-plugin-name/commands
mkdir -p plugins/your-plugin-name/examples
```

### Step 3: Create the Plugin Manifest

Create `plugins/your-plugin-name/.claude-plugin/plugin.json`:

```json
{
  "name": "your-plugin-name",
  "description": "One-sentence description of what your plugin does",
  "version": "1.0.0",
  "author": {
    "name": "Your Name",
    "email": "your@email.com"
  },
  "homepage": "https://github.com/jontoIO/claude-agents",
  "repository": "https://github.com/jontoIO/claude-agents",
  "license": "MIT",
  "keywords": [
    "keyword1",
    "keyword2",
    "keyword3",
    "keyword4"
  ]
}
```

**Tips**:
- Choose 5-10 descriptive keywords
- Use lowercase, hyphenated names
- Start at version 1.0.0

### Step 4: Create an Agent (Optional)

Create `plugins/your-plugin-name/agents/agent-name.md`:

```markdown
---
name: agent-name
description: Brief description of when to use this agent. Should be one clear sentence.
---

You are a [role] specializing in [domain]. Your expertise covers:

## Capabilities
- Capability 1: [Specific skill]
- Capability 2: [Specific skill]
- Capability 3: [Specific skill]

## Approach
1. **[Step 1 name]**: [What you do in this step]
2. **[Step 2 name]**: [What you do in this step]
3. **[Step 3 name]**: [What you do in this step]

## Knowledge
You have deep knowledge of:
- [Topic area 1]
- [Topic area 2]
- [Topic area 3]

## Available Tools
You have access to MCP tools for:
- [Tool 1]: [What it's for]
- [Tool 2]: [What it's for]

[Additional detailed instructions for the agent behavior]
```

**Tips**:
- Be specific about capabilities
- Define clear approach steps
- List relevant knowledge domains
- Mention available MCP tools if applicable

### Step 5: Create Skills

For each skill, create `plugins/your-plugin-name/skills/skill-name/SKILL.md`:

```markdown
---
name: skill-name
description: Brief description of when to use this skill. One clear sentence.
---

You are a [skill specialist]. Your goal is to [objective].

## Core Methodology

Follow this [X]-step systematic approach:

### STEP 1: [Step Name]

[Detailed instructions for this step]

**Actions**:
1. [Specific action 1]
2. [Specific action 2]
3. [Specific action 3]

**Questions to Ask** (if data unavailable):
- "[Question 1]"
- "[Question 2]"
- "[Question 3]"

**Output**: [What this step produces]

### STEP 2: [Step Name]

[Detailed instructions for this step]

[Continue for all steps...]

## Output Format

Present your results in this format:

\`\`\`markdown
# [Skill Output Title]

[Template for the output]
\`\`\`

## Examples

### Example 1: [Scenario]
[Complete worked example]

### Example 2: [Scenario]
[Complete worked example]

## Quality Checklist

Before finalizing, verify:
- [ ] Checklist item 1
- [ ] Checklist item 2
- [ ] Checklist item 3

## Tips and Best Practices

1. **Tip 1**: [Advice]
2. **Tip 2**: [Advice]
3. **Tip 3**: [Advice]
```

**Tips**:
- Skills should be structured methodologies (3-7 steps)
- Include concrete examples
- Provide output templates
- Add quality checklists
- Be specific about what to do at each step

### Step 6: Create Commands

For each command, create `plugins/your-plugin-name/commands/command-name.md`:

```markdown
# Command Name

Brief description of what this command does.

## Purpose

Use this command when:
- Scenario 1
- Scenario 2
- Scenario 3

## Usage

\`\`\`bash
/your-plugin-name:command-name [arguments]
\`\`\`

### Parameters

- `argument1`: Description of what this argument is
- `argument2`: Description of what this argument is

## Examples

### Example 1: Basic Usage

\`\`\`bash
/your-plugin-name:command-name simple argument
\`\`\`

**Expected Output**:
\`\`\`
[Sample output]
\`\`\`

### Example 2: With Parameters

\`\`\`bash
/your-plugin-name:command-name complex argument --param value
\`\`\`

**Expected Output**:
\`\`\`
[Sample output]
\`\`\`

## When NOT to Use

- Don't use if [scenario]
- Use [alternative] instead when [condition]
```

**Tips**:
- Commands should be quick operations
- Provide usage examples
- Clarify when NOT to use the command
- Document all parameters

### Step 7: Create Examples

Create realistic examples in `plugins/your-plugin-name/examples/`:

```markdown
# Example: [Scenario Name]

## Context

[Describe the scenario - who, what, why]

## Challenge

[What problem needed solving]

## Approach

[How the plugin was used]

## Results

[What outcomes were achieved]

### Detailed Walkthrough

#### Step 1: [Step Name]
[What was done]

#### Step 2: [Step Name]
[What was done]

## Key Takeaways

- Takeaway 1
- Takeaway 2
- Takeaway 3
```

### Step 8: Write Plugin README

Create `plugins/your-plugin-name/README.md`:

```markdown
# Plugin Name

One-paragraph description of what your plugin does and who it's for.

## Overview

More detailed overview of the plugin's capabilities and use cases.

## Features

- Feature 1: [Description]
- Feature 2: [Description]
- Feature 3: [Description]

## Installation

\`\`\`bash
/plugin install your-plugin-name@jontoio-claude-agents
\`\`\`

## Quick Start

[Simple example to get users started]

## Components

### Agent: agent-name

[Description of the agent and when to use it]

### Skills

- `skill-name-1`: [Brief description]
- `skill-name-2`: [Brief description]

### Commands

- `command-name-1`: [Brief description]
- `command-name-2`: [Brief description]

## Usage Examples

### Example 1: [Use Case]

\`\`\`bash
[Commands or usage]
\`\`\`

[Explanation]

### Example 2: [Use Case]

\`\`\`bash
[Commands or usage]
\`\`\`

[Explanation]

## Complete Examples

See the [examples/](./examples/) directory for detailed walkthroughs:
- [Example 1](./examples/example-1.md)
- [Example 2](./examples/example-2.md)

## Tips for Best Results

1. **Tip 1**: [Advice]
2. **Tip 2**: [Advice]
3. **Tip 3**: [Advice]

## Limitations

- Limitation 1
- Limitation 2
- Limitation 3

## Version History

See [CHANGELOG.md](./CHANGELOG.md) for version history.

## Contributing

Contributions welcome! See [CONTRIBUTING.md](../../CONTRIBUTING.md).

## License

MIT - See [LICENSE](../../LICENSE) for details.
```

### Step 9: Create CHANGELOG

Create `plugins/your-plugin-name/CHANGELOG.md`:

```markdown
# Changelog

All notable changes to this plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - YYYY-MM-DD

### Added
- Initial release
- [Agent name] agent
- [Skill 1] skill
- [Skill 2] skill
- [Command 1] command
- Comprehensive documentation and examples
```

## Testing Your Plugin

### Local Testing

1. **Add the marketplace locally**:
   ```bash
   /plugin marketplace add ./
   ```

2. **Install your plugin**:
   ```bash
   /plugin install your-plugin-name@jontoio-claude-agents
   ```

3. **Verify components**:
   ```bash
   /plugin  # Should show your plugin
   /agents  # Should show your agent (if applicable)
   ```

4. **Test each component**:
   ```bash
   # Test skills
   /your-plugin-name:skill-name

   # Test commands
   /your-plugin-name:command-name
   ```

### Testing Checklist

- [ ] Plugin installs without errors
- [ ] Agent appears in `/agents` (if applicable)
- [ ] All skills can be invoked
- [ ] All commands work as documented
- [ ] Examples in README produce expected results
- [ ] No broken links in documentation
- [ ] Frontmatter YAML is valid
- [ ] JSON manifest is valid

## Publishing Your Plugin

### Update Marketplace Manifest

Add your plugin to `.claude-plugin/marketplace.json`:

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

### Update Root README

Add your plugin to the "Available Plugins" section in the root README.md.

### Submit Pull Request

1. Commit your changes
2. Push to your fork
3. Open a pull request
4. Provide clear description of what your plugin does
5. Include screenshots or examples if helpful

## Best Practices

### Writing Effective Skills

1. **Structure is key**: Use numbered steps (3-7 steps ideal)
2. **Be specific**: "Calculate X using formula Y" not "analyze the data"
3. **Provide templates**: Show the exact format of outputs
4. **Include examples**: Real scenarios with complete outputs
5. **Add checklists**: Help users verify completeness

### Writing Effective Agents

1. **Clear persona**: Define expertise domain clearly
2. **Systematic approach**: Outline methodology steps
3. **Tool awareness**: Mention available MCP tools
4. **Balanced instructions**: Detailed but not overwhelming

### Writing Effective Commands

1. **Single purpose**: One command = one specific action
2. **Quick to execute**: Commands should be fast
3. **Clear parameters**: Document all options
4. **When not to use**: Help users choose correctly

### Documentation Tips

1. **Write for beginners**: Assume no prior knowledge
2. **Show, don't tell**: Use examples liberally
3. **Be consistent**: Follow the same structure throughout
4. **Test your docs**: Have someone else follow them

### Quality Standards

1. **Accuracy**: Test everything thoroughly
2. **Completeness**: Cover all use cases
3. **Clarity**: Use simple, direct language
4. **Maintenance**: Keep documentation updated

## Troubleshooting

### Plugin Won't Install

- Check JSON syntax in `plugin.json`
- Verify directory structure matches requirements
- Ensure YAML frontmatter is valid

### Agent Doesn't Appear

- Check YAML frontmatter in agent file
- Verify file is in `agents/` directory
- Ensure `.md` extension is present

### Skill Doesn't Work

- Check YAML frontmatter syntax
- Verify `SKILL.md` filename (must be uppercase)
- Ensure file is in `skills/skill-name/SKILL.md`

### Command Not Found

- Verify file is in `commands/` directory
- Check command name matches filename
- Ensure proper namespacing used

## Examples and Templates

See the `financial-advisor` plugin as a reference implementation:
- [Plugin Structure](../plugins/financial-advisor/)
- [Agent Example](../plugins/financial-advisor/agents/financial-advisor.md)
- [Skill Example](../plugins/financial-advisor/skills/cost-estimation/SKILL.md)
- [Command Example](../plugins/financial-advisor/commands/quick-cost-estimate.md)

## Additional Resources

- [CONTRIBUTING.md](../CONTRIBUTING.md) - Contribution guidelines
- [Marketplace Setup Guide](./marketplace-setup.md) - How to use the marketplace
- [Claude Code Documentation](https://github.com/anthropics/claude-code)

## Getting Help

- Open an issue for questions
- Check existing plugins for examples
- Reach out to maintainers for guidance

Happy plugin building!
