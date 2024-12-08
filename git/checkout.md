# Git Checkout
The `git checkout` command is one of the original Git commands used to switch branches, restore files, or even inspect past commits. While it's still widely used, some of its functionality has been split into newer commands like `git switch` and `git restore` for better clarity.

## What is `git checkout`
`git checkout` is a multi-purpose command that allows you to:
1. Switch Between Branches
2. Restore Files
3. Navigate to Specific Commits

## Switch to an Existing Branch
```bash
git checkout <branch_name>
```
- Changes the working directory to match the specified branch.
- Update the `HEAD` pointer to the new branch.

## Create and Switch to a New Branch
```bash
git checkout -b <new_branch_name>
```
- Creates a new branch and switches to it in one step.

## Restore a Specific File
```bash
git checkout <branch_name> -- <file_name>
```
- Restores a specific file from the specified branch to your working directory

Example: 
```bash
git checkout main -- README.md
```
This replaces your current version of `README.md` with the version from the `main` branch.

## Navigate to a Specific Commit
```bash
git  checkout <commit_hash>
```
- Update the working directory to reflect the state of the repository at the specified commit.
- **Detached Head State:** When you checkout a commit, Git enters a *detached HEAD* state. Changes made here will not belong to any branch unless explicitly committed to a new branch.

## Create and Checkout to a new branch from a specific commit
```bash
git checkout -b <branch_name> <commit_hash>
```

## Use `git switch` or `git restore`:
- Git introduced `git switch` and `git restore` in newer versions to reduce confusion:
- `git switch`: For Switching branches.
- `git restore`: For restoring files or commits.
