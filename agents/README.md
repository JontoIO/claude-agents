# Agents

This directory contains complete agent configurations that can be used with Claude.

## What is an Agent?

An agent is a complete configuration that defines Claude's behavior, persona, and capabilities for a specific use case.

## Structure

Each agent should be in its own directory with the following structure:

```
agent-name/
├── README.md        # Description and usage instructions
├── config.json      # Agent configuration (optional)
└── examples/        # Usage examples (optional)
```

## Creating a New Agent

1. Create a new directory with a descriptive name (use lowercase with hyphens)
2. Add a README.md describing the agent's purpose and capabilities
3. Include usage examples
4. Optionally add a config.json with agent settings

## Example

See the [examples](../examples) directory for sample agent implementations.

## Contributing

Please read [CONTRIBUTING.md](../CONTRIBUTING.md) before submitting new agents.
