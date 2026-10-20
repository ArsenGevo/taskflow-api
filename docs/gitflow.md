# Git Flow

## 1. Main Branches

- `main` — the main project branch (production).
- `develop` — the integration branch for ongoing development.

The `main` and `develop` branches are intended to be associated with their respective CI/CD environments.

## 2. Branch Naming Conventions

Feature branches must follow this naming convention:

`{JIRA_TASK_KEY}-{short-description}`

Example:

`SCRUM-12-repository-setup`

Branch names must include the corresponding Jira issue key and a short, descriptive name in English.

## 3. Branch Creation Rules

Each new working branch must be created from `main`.

### Exception: Subtasks Within a Story

If multiple subtasks belong to the same Story, a separate parent branch is created from `main`.

Individual subtask branches are then created from the parent Story branch.

Example:

```text
main
  |
  └── SCRUM-11-local-env
        |
        ├── SCRUM-16-...
        ├── SCRUM-17-...
        ├── SCRUM-18-...
        └── SCRUM-19-...
```

Pull Requests for individual subtasks must target the parent Story branch.

Once all subtasks are completed and reviewed, the parent Story branch can be merged into `main`.

## 4. Commit Message Conventions

Each commit must contain a logically consistent set of changes.

Commit messages must follow this format:

`{JIRA_TASK_KEY} - {description}.`

Examples:

- `SCRUM-12 - Added initial repository structure.`
- `SCRUM-12 - Added Git workflow documentation.`

Commit messages should clearly and concisely describe the changes made.

Avoid combining unrelated changes in a single commit.

## 5. Pull Requests

All changes must be submitted through Pull Requests.

### Target Branch

- Regular feature branches must target `main`.
- Subtask branches belonging to a Story with a dedicated parent branch must target that parent Story branch.

### Pull Request Description

Each Pull Request must include:

- A brief summary of the changes.
- A reference to the corresponding Jira issue.
- Any relevant additional information for reviewers.

## 6. Code Review

All Pull Requests must be reviewed before merging.

The following rules apply:

1. A Pull Request must receive approval from a reviewer before it can be merged.
2. If changes are requested, the developer must address the feedback.
3. Additional changes must be pushed to the same branch to update the existing Pull Request.
4. Merging is allowed only after the required approval has been received.

## 7. Merge Rules

Changes must not be merged directly into `main` without Code Review.

The standard workflow is:

```text
main
  |
  └── SCRUM-12-repository-setup
           |
           ├── Implement changes
           |
           ├── Commit changes
           |
           ├── Push branch
           |
           ├── Create Pull Request
           |
           ├── Code Review
           |
           └── Merge into main
```

After a successful merge, the corresponding Jira issue can be moved to Done, provided all Acceptance Criteria have been met.
