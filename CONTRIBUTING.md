# Contributing to Claude Agents Collection

Thank you for your interest in contributing to the Claude Agents Collection! This document provides guidelines for contributing agents, skills, and commands.

## 📋 How to Contribute

### 1. Fork and Clone

1. Fork this repository
2. Clone your fork locally
3. Create a new branch for your contribution

### 2. Choose What to Contribute

- **Agents**: Complete agent configurations with specific personas
- **Skills**: Modular abilities that extend agent capabilities
- **Commands**: Specific prompts for common tasks

### 3. Follow the Structure

#### For Agents (`/agents`)

Create a new directory with your agent name:

```
agents/
└── your-agent-name/
    ├── README.md        # Agent description and usage
    ├── config.json      # Agent configuration
    └── examples/        # Usage examples
```

#### For Skills (`/skills`)

Create a new directory with your skill name:

```
skills/
└── your-skill-name/
    ├── README.md        # Skill description
    └── skill.md         # Skill definition
```

#### For Commands (`/commands`)

Create a markdown file for your command:

```
commands/
└── your-command.md      # Command description and prompt
```

## ✅ Submission Guidelines

### Quality Standards

- **Documentation**: Include clear README files with usage examples
- **Naming**: Use descriptive, lowercase names with hyphens (e.g., `data-analyst-agent`)
- **Testing**: Verify your contribution works as expected
- **Attribution**: Credit sources and inspirations when applicable

### Content Requirements

1. **Clear Purpose**: Explain what the agent/skill/command does
2. **Usage Examples**: Provide practical examples
3. **Dependencies**: List any required tools or resources
4. **Limitations**: Document known limitations or constraints

### Pull Request Process

1. Ensure your contribution follows the structure above
2. Update the main README.md if you're adding a new category
3. Write a clear PR description explaining your contribution
4. Reference any related issues

## 🚫 What Not to Include

- Personal or sensitive information
- Copyrighted content without permission
- Malicious or harmful prompts
- Overly specific or single-use configurations

## 📝 Code of Conduct

Please be respectful and constructive in all interactions. We aim to maintain a welcoming community for all contributors.

## 💡 Need Help?

- Open an issue for questions
- Check existing agents/skills/commands for examples
- Reach out to maintainers for guidance

## 🔄 Review Process

Contributions will be reviewed for:
- Quality and usefulness
- Documentation completeness
- Adherence to guidelines
- No conflicts with existing content

Thank you for contributing to the Claude Agents Collection!
