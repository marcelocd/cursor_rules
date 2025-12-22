# Commit Organizer

## Description
Group related changes, stage them to the git index, and generate a commit message following conventional commit format. This command stages files but does NOT commit - it only stages changes and populates the commit message field for your review.

## Usage
```
@commit
```

Or with explicit branch name:
```
@commit MCD-1993
```

## Instructions

When invoked:

1. **Detect branch name** (if not provided):
   Run `git branch --show-current` to get the current branch name.
   Extract the ticket ID (e.g., `MCD-1993` from `feature/MCD-1993-add-validation`).

2. **Get current changes**:
   Run `git status` to see both staged and unstaged changes.
   Run `git diff --staged` to see what's already staged.
   Run `git diff` to see what's unstaged.

3. **Determine next set of changes to stage**:
   - If there are already staged changes, generate a commit message for those staged changes (skip to step 5, do not stage additional files).
   - If there are no staged changes, analyze unstaged changes and group related changes into logical commits (by feature, file type, or concern).
   - Select the FIRST logical group of changes that should be committed next.

4. **Stage the selected changes**:
   Run `git add` with the specific files/paths for the selected group of changes.
   DO NOT run `git commit` - only stage the changes.

5. **Generate commit message** following the conventions defined in:
   `~/.cursor/rules/commit-message-convention/RULE.md`
   - **Important**: The imperative verb at the beginning of the subject line (after the type prefix) must always be capitalized.
   - Example: `test: Add tests` (not `test: add tests`)

6. **Populate the commit message field** in Cursor with the generated message:
   - If branch name is `master` or `stage`, use format:
     ```
     <subject line>

     * <detail>
     * <detail>
     ```
   - Otherwise, use format:
     ```
     [{BRANCH_NAME}] <subject line>

     * <detail>
     * <detail>
     ```

7. **List the files that were staged** for reference:
   - `path/to/file1.ts`
   - `path/to/file2.ts`

**Important Notes:**
- This command stages files and generates a commit message - it does NOT commit.
- This command does NOT create, update, or delete any files on disk - it only stages existing changes.
- The user will review the staged changes and commit message, then manually commit if satisfied.
- When run again, it will work on the NEXT set of changes (either commit the already-staged changes first, or stage the next logical group if nothing is staged).

---

## Branch Name Detection

Common branch naming patterns to extract ticket ID from:
- `MCD-1993` → `MCD-1993`
- `feature/MCD-1993-description` → `MCD-1993`
- `fix/MCD-1993-bug-fix` → `MCD-1993`
- `MCD-1993/some-feature` → `MCD-1993`

Regex pattern: `([A-Z]+-\d+)`

If no ticket ID is found, use the full branch name or ask the user.

---

## Grouping Strategy
- Group by logical unit of work
- Separate refactors from features
- Separate test changes from implementation (unless tightly coupled)
- Keep configuration changes in their own commit when possible
- Dependencies changes should be in their own commit and should be commited first if there are any
