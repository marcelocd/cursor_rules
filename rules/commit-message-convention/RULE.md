---
description: "This rule provides standards for commit messages"
alwaysIntelligently: true
---

# Commit Message Convention

## Format

Each commit should follow this structure:

**For branches other than `master` or `main`:**
```
[{BRANCH_NAME}] Imperative short sentence (50 chars max)

* Concise detailed information
* More details if needed
```

**For `master` or `main` branches:**
```
Imperative short sentence (50 chars max)

* Concise detailed information
* More details if needed
```

## Rules

### Subject Line
- **Prefix**: Include the branch/ticket name in brackets (e.g., `[MCD-1993]`) only when the branch is NOT `master` or `main`. For `master` or `main` branches, omit the prefix.
- **Length**: Keep the subject line to 50 characters or less (excluding the prefix if present)
- **Style**: Use imperative mood ("Add feature" not "Added feature" or "Adds feature")
- **No period**: Don't end the subject line with a period

### Body (Optional)
- Separate from subject with a blank line
- Use bullet points (`*`) for detailed information
- Explain **what** and **why**, not **how**
- Wrap lines at 72 characters

### Grouping Strategy
- Group by logical unit of work
- Separate refactors from features
- Separate test changes from implementation (unless tightly coupled)
- Keep configuration changes in their own commit when possible

## Examples

### Commit #1 (on feature branch)
```
[MCD-1993] Add payment validation for subscriptions

* Validate card expiration before processing
* Return descriptive error messages to UI
```

### Commit #2 (on feature branch)
```
[MCD-1993] Update error handling in checkout flow

* Handle network timeout gracefully
* Add retry logic for failed transactions
```

### Commit #3 (on feature branch, simple change, no body needed)
```
[MCD-1993] Fix typo in subscription confirmation
```

### Commit #4 (on master/main branch)
```
Add payment validation for subscriptions

* Validate card expiration before processing
* Return descriptive error messages to UI
```

### Commit #5 (on master/main branch, simple change, no body needed)
```
Fix typo in subscription confirmation
```

## Imperative Mood Examples

| ✅ Do | ❌ Don't |
|-------|----------|
| Add validation | Added validation |
| Fix bug in cart | Fixes bug in cart |
| Update dependencies | Updated dependencies |
| Remove deprecated code | Removing deprecated code |

## Quick Template

**For branches other than `master` or `main`:**
```
[{BRANCH_NAME}] <verb> <what you changed>

* <why or additional context>
* <related changes if any>
```

**For `master` or `main` branches:**
```
<verb> <what you changed>

* <why or additional context>
* <related changes if any>
```
