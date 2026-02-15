# Claude Agents Marketplace Setup Guide

This guide explains how to add and use the Claude Agents Marketplace with Claude Code.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Adding the Marketplace](#adding-the-marketplace)
- [Installing Plugins](#installing-plugins)
- [Using Plugins](#using-plugins)
- [Managing Plugins](#managing-plugins)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before using this marketplace, ensure you have:

1. **Claude Code** installed and working
   - Download from: https://github.com/anthropics/claude-code
   - Follow installation instructions for your platform

2. **Internet Connection** (for remote marketplace)
   - Or clone the repository for local use

## Adding the Marketplace

### Option 1: Remote Marketplace (Recommended)

Add the marketplace from GitHub:

```bash
/plugin marketplace add jontoIO/claude-agents
```

This connects to the live repository and automatically gets updates when new plugins are added.

### Option 2: Local Marketplace

Clone the repository and add it locally:

```bash
# Clone the repository
git clone https://github.com/jontoIO/claude-agents.git
cd claude-agents

# Add the local marketplace
/plugin marketplace add ./
```

This is useful for:
- Testing plugin development
- Working offline
- Using a specific version

### Verify Marketplace

Check that the marketplace was added:

```bash
/plugin
```

You should see `jontoio-claude-agents` in the list of marketplaces.

## Installing Plugins

### List Available Plugins

View all plugins in the marketplace:

```bash
/plugin
```

This shows:
- Plugin names
- Descriptions
- Versions
- Installation status

### Install a Plugin

Install the financial advisor plugin:

```bash
/plugin install financial-advisor@jontoio-claude-agents
```

**Format**: `/plugin install <plugin-name>@<marketplace-name>`

### Verify Installation

After installation, verify the plugin is active:

```bash
/plugin
```

The plugin should show as "Installed" or "Active".

## Using Plugins

### Using Agents

Plugins can provide specialized agents. View available agents:

```bash
/agents
```

To use an agent:
1. Select it from the agents list
2. Claude will adopt that agent's persona and capabilities
3. The agent persists for the conversation

**Example**: The financial-advisor agent

```bash
# View agents
/agents

# Select financial-advisor
# [User selects from UI]

# Now Claude acts as a financial advisor
"Please estimate the costs for my SaaS project"
```

### Using Skills

Skills are structured methodologies provided by plugins. Invoke a skill:

```bash
/plugin-name:skill-name
```

**Example**: Cost estimation skill

```bash
/financial-advisor:cost-estimation
```

Claude will:
1. Follow the skill's methodology (e.g., 5-step framework)
2. Gather data (read files, ask questions)
3. Perform analysis
4. Provide structured output

### Using Commands

Commands are quick actions for specific tasks:

```bash
/plugin-name:command-name [arguments]
```

**Example**: Quick cost estimate

```bash
# Basic usage
/financial-advisor:quick-cost-estimate Add AI chat feature

# With parameters
/financial-advisor:quick-cost-estimate Add real-time collaboration --users 5000 --timeline "3 months"
```

## Plugin Namespacing

All plugin components are namespaced to avoid conflicts:

```
/plugin-name:component-name
```

**Examples**:
- `/financial-advisor:cost-estimation` (skill)
- `/financial-advisor:quick-cost-estimate` (command)
- `/code-reviewer:review-pr` (hypothetical command)
- `/security-auditor:vulnerability-scan` (hypothetical skill)

This ensures plugins don't interfere with each other.

## Managing Plugins

### Update a Plugin

If a plugin has updates:

```bash
/plugin update financial-advisor@jontoio-claude-agents
```

### Uninstall a Plugin

Remove a plugin:

```bash
/plugin uninstall financial-advisor@jontoio-claude-agents
```

### List Installed Plugins

See all installed plugins:

```bash
/plugin
```

### View Plugin Details

Get information about a specific plugin:

```bash
/plugin info financial-advisor@jontoio-claude-agents
```

This shows:
- Version
- Description
- Components (agents, skills, commands)
- Documentation link

## Example Workflow

Here's a complete workflow using the financial-advisor plugin:

### 1. Add Marketplace and Install Plugin

```bash
# Add marketplace
/plugin marketplace add jontoIO/claude-agents

# Install plugin
/plugin install financial-advisor@jontoio-claude-agents
```

### 2. Get a Quick Estimate

```bash
/financial-advisor:quick-cost-estimate Add user authentication with Auth0
```

Claude provides a rapid estimate with API costs, development time, and ongoing expenses.

### 3. Full Cost Analysis

For a detailed analysis:

```bash
/financial-advisor:cost-estimation
```

Claude will:
- Ask about your project (tech stack, users, team)
- Analyze repository files if available
- Calculate costs across all categories
- Model low/medium/high scenarios
- Provide optimization recommendations

### 4. Risk Assessment

Identify financial risks:

```bash
/financial-advisor:financial-risk-assessment
```

Claude will:
- Check compliance requirements (GDPR, HIPAA, etc.)
- Identify cost overrun risks
- Assess integration dependencies
- Propose mitigation strategies

### 5. ROI Analysis

Calculate return on investment:

```bash
/financial-advisor:roi-analysis
```

Claude will:
- Calculate investment costs
- Estimate returns
- Determine break-even point
- Model scenarios
- Provide go/no-go recommendation

## Tips for Best Results

### 1. Provide Context

The more context you provide, the better the results:

```bash
# Less context (okay)
/financial-advisor:cost-estimation

# More context (better)
"I'm building a SaaS app with React, Node.js, and PostgreSQL.
We expect 1,000 users initially and plan to use Claude API for
AI features. I have a team of 2 developers. Please estimate costs."
/financial-advisor:cost-estimation
```

### 2. Let Skills Guide You

Skills will ask questions if they need more information. Answer them to get accurate results.

### 3. Use Commands for Quick Answers

If you need a quick answer, use commands:
- `/financial-advisor:quick-cost-estimate` for rapid estimates

For detailed analysis, use skills:
- `/financial-advisor:cost-estimation` for comprehensive breakdowns

### 4. Combine Plugin Features

Use multiple features together:

1. Quick estimate → Determine if project is viable
2. Cost estimation → Get detailed breakdown
3. Risk assessment → Identify potential issues
4. ROI analysis → Make go/no-go decision
5. Monetization planning → Design pricing strategy

### 5. Reference Documentation

Each plugin has comprehensive documentation:

```bash
# View plugin README
# (Navigate to GitHub or local clone)
cat plugins/financial-advisor/README.md

# View examples
cat plugins/financial-advisor/examples/saas-startup.md
```

## Troubleshooting

### Marketplace Won't Add

**Issue**: Error when adding marketplace

**Solutions**:
- Check internet connection (for remote marketplace)
- Verify GitHub repository exists: https://github.com/jontoIO/claude-agents
- Try local marketplace: Clone repo and use `/plugin marketplace add ./`
- Check Claude Code is up to date

### Plugin Won't Install

**Issue**: Error when installing plugin

**Solutions**:
- Verify marketplace is added: `/plugin`
- Check plugin name is correct: `financial-advisor` (not `Financial-Advisor`)
- Ensure marketplace name is correct: `@jontoio-claude-agents`
- Try refreshing marketplace: `/plugin marketplace refresh jontoio-claude-agents`

### Command Not Found

**Issue**: `/plugin-name:command-name` doesn't work

**Solutions**:
- Verify plugin is installed: `/plugin`
- Check command name spelling
- Ensure using correct namespace: `/financial-advisor:quick-cost-estimate`
- Try reinstalling plugin

### Agent Not Appearing

**Issue**: Agent doesn't show in `/agents`

**Solutions**:
- Verify plugin is installed
- Restart Claude Code
- Check plugin has agents (some plugins might not include agents)

### Skill Doesn't Execute

**Issue**: Skill invoked but doesn't work as expected

**Solutions**:
- Verify syntax: `/plugin-name:skill-name` (colon, not slash)
- Check for typos in skill name
- Ensure plugin is properly installed
- Try providing more context in your message

## Advanced Usage

### Multiple Plugins

You can install multiple plugins and use them together:

```bash
# Install multiple plugins
/plugin install financial-advisor@jontoio-claude-agents
/plugin install code-reviewer@jontoio-claude-agents  # (hypothetical)

# Use them together
/financial-advisor:cost-estimation
# Then
/code-reviewer:review-architecture
```

### Switching Agents

Switch between agents as needed:

```bash
/agents  # Select financial-advisor
"Estimate costs for my project"

/agents  # Switch to code-reviewer (hypothetical)
"Review my authentication code"
```

### Custom Workflows

Create workflows combining plugins:

1. **Project Planning Workflow**:
   - Cost estimation → Budget approval
   - Risk assessment → Risk mitigation plan
   - ROI analysis → Project justification
   - Monetization planning → Pricing strategy

2. **Feature Development Workflow**:
   - Quick cost estimate → Go/no-go decision
   - Development → Implementation
   - Code review → Quality assurance
   - Testing → Deployment

## Getting Help

### Plugin-Specific Help

Each plugin has documentation:
- **README**: https://github.com/jontoIO/claude-agents/tree/main/plugins/financial-advisor
- **Examples**: Check the `examples/` directory
- **Issues**: Report at https://github.com/jontoIO/claude-agents/issues

### General Help

- Claude Code docs: https://github.com/anthropics/claude-code
- Marketplace issues: https://github.com/jontoIO/claude-agents/issues
- Plugin development: See [Creating Plugins Guide](./creating-plugins.md)

## FAQ

### Q: Do plugins cost money?

A: No, all plugins in this marketplace are free and open source (MIT License).

### Q: Can I create my own plugin?

A: Yes! See the [Creating Plugins Guide](./creating-plugins.md) for instructions.

### Q: Are plugins safe?

A: Plugins in this marketplace are reviewed before acceptance. However, always review plugin code before installation if you have security concerns.

### Q: Can plugins access my files?

A: Plugins use the same permissions as Claude Code. They can only access files you've granted Claude Code permission to access.

### Q: How do I update plugins?

A: Use `/plugin update plugin-name@marketplace-name` or reinstall the plugin.

### Q: Can I use plugins offline?

A: If you clone the repository locally and add it as a local marketplace, yes. However, you won't get automatic updates.

### Q: How do I contribute a plugin?

A: See [CONTRIBUTING.md](../CONTRIBUTING.md) for the full contribution process.

## Next Steps

Now that you've set up the marketplace:

1. **Try the Financial Advisor Plugin**: Start with a quick cost estimate
2. **Explore Examples**: Check out detailed walkthroughs in plugin examples
3. **Create Your Own Plugin**: See the [Creating Plugins Guide](./creating-plugins.md)
4. **Contribute**: Share improvements or new plugins with the community

Happy building!
