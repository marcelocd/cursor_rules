# Code Review

## Overview

Perform a thorough code review that verifies functionality, maintainability, and
security before approving a change. Focus on architecture, readability,
performance implications, and provide actionable suggestions for improvement.

**Important**: Only review files that are currently unstaged in git. Output all findings directly in the chat in a concise and readable format - do not generate any review files.

## Steps

1. **Identify unstaged files**
    - Use git to identify only unstaged (modified but not staged) files
    - Review only these files, ignoring staged and committed changes
2. **Understand the change**
    - Read the unstaged changes to understand what was modified
    - Identify the scope of files and features impacted
    - Note any assumptions or questions to clarify with the author
3. **Validate functionality**
    - Confirm the code delivers the intended behavior
    - Exercise edge cases or guard conditions mentally or by running locally
    - Check error handling paths and logging for clarity
4. **Assess quality**
    - Ensure functions are focused, names are descriptive, and code is readable
    - Watch for duplication, dead code, or missing tests
    - Verify documentation and comments reflect the latest changes
5. **Review security and risk**
    - Look for injection points, insecure defaults, or missing validation
    - Confirm secrets or credentials are not exposed
    - Evaluate performance or scalability impacts of the change
6. **Output findings**
    - Present all findings directly in the chat conversation
    - Use a concise, readable format with clear sections
    - Do not create or save any review files

## Review Checklist

### Functionality

- [ ] Intended behavior works and matches requirements
- [ ] Edge cases handled gracefully
- [ ] Error handling is appropriate and informative

### Code Quality

- [ ] Code structure is clear and maintainable
- [ ] No unnecessary duplication or dead code
- [ ] Tests/documentation updated as needed

### Security & Safety

- [ ] No obvious security vulnerabilities introduced
- [ ] Inputs validated and outputs sanitized
- [ ] Sensitive data handled correctly

## Additional Review Notes

- Architecture and design decisions considered
- Performance bottlenecks or regressions assessed
- Coding standards and best practices followed
- Resource management, error handling, and logging reviewed
- Suggested alternatives, additional test cases, or documentation updates
  captured

## Output Format

Provide constructive feedback with concrete examples and actionable guidance directly in the chat conversation. Use a clear, concise format such as:

- Summary of changes reviewed
- Findings organized by category (Functionality, Code Quality, Security)
- Specific file and line references where applicable
- Actionable recommendations

Do not create or save any review files - all output should appear in the chat.
