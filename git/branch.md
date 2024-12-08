# Git Branch
Git branches are a core feature that allows you to work on different versions of your project simultaneously. They enable efficient workflows for collaboration, experimentation, and version control.

## What Is a Git Branch?

- A branch is a pointer to a specific commit in your project's history.
- It acts as an independent timeline where you can make changes without affecting the main codebase.
- Default Branch: Most repositories start with a default branch named main (or master in older setups).

## Why Use Branches?

- Isolate Workflows: Keep feature development, bug fixes, and experiments separate.
- Collaboration: Team members can work on different branches without conflict.
- Versioning: Manage multiple versions of a project (e.g., stable releases and development versions).


## View Branches

### List Local Branches:
```bash
git branch
```
- Shows all local branches
- The current branch is marked with an asterisk (`*`).

### List Remote Branches:
```bash
git branch -r
```

### List All Branches (Local and Remote):
```bash
git branch -a
```

## Create a New Branch
```bash
git branch <branch_name>
```
- create a new branch from the current commit.

## Switch to a Branch
```bash
git switch <branch_name>
```
OR

```bash
git checkout <branch_name>
```
- Changes your working directory to the specified branch.

## Create and Switch to a Branch
```bash
git switch -c <branch_name>
```
OR

```bash
git checkout -b <branch_name>
```
- Create and switches to the new branch in one step.

> Refer [Checkout command in Git](./checkout.md)

## Rename a Branch
- Rename Current Branch:
```bash
git branch -m <new_name>
```
- Renmae a Specific Branch:
```bash
git branch -m <old_name> <new_name>
```

## Delete a Branch
- Delete a Local Branch:
```bash
git branch -d <branch_name>
```
> Fails if the branch has unmerged changes.

- Force-Delete a Branch:
```bash
git branch -D <branch_name>
```

- Delete a Remote Branch:
```bash
git push origin --delete <branch_name>
```

## Merge Branches
- Merge a Branch into the Current Branch:
```bash
git merge <branch_name>
```
- Combines changes from `<branch_name>` into the branch you are currently on.
- **Resolve conflicts:** If there are conflicts during a merge, Git will prompt you to resolve them manually.

