# Example Agent - Code Reviewer

## Description

This is an example agent that demonstrates how to structure an agent for code review tasks. This agent helps review code for quality, bugs, and best practices.

## Purpose

The Code Reviewer agent is designed to:
- Analyze code for potential bugs and issues
- Check adherence to coding standards
- Suggest improvements and optimizations
- Provide constructive feedback

## Usage

Use this agent when you need:
- Code review before merging pull requests
- Quality checks on new code
- Suggestions for refactoring
- Security vulnerability scanning

## Configuration

This agent uses the following capabilities:
- Code analysis
- Pattern recognition
- Best practice knowledge
- Security awareness

## Example Interaction

**User**: Please review this Python function:

```python
def calculate_total(items):
    total = 0
    for item in items:
        total = total + item['price']
    return total
```

**Agent**: I'll review this function. Here are my observations:

**Positive aspects:**
- Clear function name and purpose
- Simple and readable logic

**Suggestions for improvement:**
1. Add type hints for better code documentation
2. Add error handling for missing 'price' key
3. Consider using sum() with a generator for more Pythonic code
4. Add docstring to explain parameters and return value

**Improved version:**
```python
def calculate_total(items: list[dict]) -> float:
    """
    Calculate the total price from a list of items.
    
    Args:
        items: List of dictionaries, each containing a 'price' key
        
    Returns:
        The sum of all item prices
        
    Raises:
        KeyError: If an item doesn't have a 'price' key
    """
    return sum(item['price'] for item in items)
```

## Limitations

- Focuses on general code quality, not domain-specific requirements
- May not catch all edge cases without full context
- Requires clear, well-formatted code input

## Customization

You can customize this agent by:
- Adding specific coding standards for your language
- Including your team's style guide
- Adding focus areas (performance, security, etc.)

## Contributing

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for guidelines on improving this agent.
