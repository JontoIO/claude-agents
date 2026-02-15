# Commands

This directory contains standalone commands and prompts for specific tasks.

## What is a Command?

A command is a specific prompt or instruction for Claude to perform a particular task. Commands are typically single-purpose and focused.

## Structure

Each command is a markdown file:

```
command-name.md      # Command description and prompt
```

## Creating a New Command

1. Create a markdown file with a descriptive name (use lowercase with hyphens)
2. Include:
   - Clear description of what the command does
   - The prompt or instruction
   - Usage examples
   - Expected outputs
   - Any prerequisites or requirements

## Example Commands

Common command categories:

- **Code Review**: Prompts for reviewing code quality
- **Documentation**: Commands for generating documentation
- **Debugging**: Instructions for debugging assistance
- **Refactoring**: Prompts for code refactoring
- **Testing**: Commands for test generation
- **Analysis**: Prompts for analyzing text, data, or code

## Format

```markdown
# Command Name

## Description
Brief description of what this command does.

## Usage
\```
[Your prompt/instruction here]
\```

## Example
Example input and expected output.

## Notes
Any additional information or tips.
```

## Contributing

Please read [CONTRIBUTING.md](../CONTRIBUTING.md) before submitting new commands.
