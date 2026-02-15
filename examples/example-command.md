# Example Command - Generate API Documentation

## Description

This command generates comprehensive API documentation from code snippets or function signatures.

## Purpose

Use this command when you need to:
- Document API endpoints
- Create function documentation
- Generate usage examples
- Produce developer-friendly docs

## Command

```
Analyze the following [code/function/API endpoint] and generate comprehensive documentation including:

1. Overview and purpose
2. Parameters/inputs with types and descriptions
3. Return values/outputs with types
4. Usage examples with sample code
5. Error handling and edge cases
6. Notes on performance or security considerations

Code to document:
[INSERT CODE HERE]

Format the documentation in [Markdown/JSDoc/Sphinx/etc.] style.
```

## Usage Example

### Input

```
Analyze the following function and generate comprehensive documentation:

def fetch_user_data(user_id: int, include_posts: bool = False) -> dict:
    user = database.get_user(user_id)
    if include_posts:
        user['posts'] = database.get_user_posts(user_id)
    return user

Format the documentation in Markdown style.
```

### Expected Output

```markdown
# fetch_user_data

## Overview
Retrieves user data from the database with optional post inclusion.

## Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| user_id | int | Yes | - | The unique identifier of the user to fetch |
| include_posts | bool | No | False | Whether to include the user's posts in the response |

## Returns

**Type:** `dict`

A dictionary containing user information with the following structure:
- `id`: User's unique identifier
- `name`: User's display name
- `email`: User's email address
- `posts`: (Optional) List of user's posts if include_posts is True

## Usage Examples

### Basic Usage
\```python
# Fetch user without posts
user = fetch_user_data(user_id=123)
print(user['name'])
\```

### With Posts
\```python
# Fetch user with posts included
user_with_posts = fetch_user_data(user_id=123, include_posts=True)
for post in user_with_posts['posts']:
    print(post['title'])
\```

## Error Handling

- Raises `UserNotFoundException` if user_id doesn't exist
- Raises `DatabaseConnectionError` if database is unavailable
- Returns empty posts list if include_posts is True but user has no posts

## Performance Considerations

- Including posts makes an additional database query
- Consider using pagination for users with many posts
- Cache results for frequently accessed users

## Security Notes

- Ensure user_id is validated before database query to prevent SQL injection
- Implement access control checks before returning user data
- Consider data privacy regulations when exposing user information
```

## Variations

### For REST APIs
```
Document this REST API endpoint including HTTP method, URL path, request/response formats, status codes, and authentication requirements:

[INSERT API ENDPOINT DETAILS]
```

### For Classes
```
Generate class documentation including constructor, methods, properties, and usage examples:

[INSERT CLASS CODE]
```

## Tips

1. **Provide context**: Include relevant imports or dependencies
2. **Specify format**: Request specific documentation style (Markdown, JSDoc, etc.)
3. **Include examples**: The more context you provide, the better the documentation
4. **Mention standards**: Reference any style guides or documentation standards to follow

## Notes

- Works best with clear, well-structured code
- Can generate documentation for various programming languages
- Adapt the prompt for your specific documentation needs
- Review and adjust generated documentation for accuracy
