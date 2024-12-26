

# Git Commit

The git commit command is used to save changes to the local Git repository. It acts like a snapshot, capturing the current state of the files you've staged, along with a message describing the changes. This helps track your project's history and progress.

usage:
```bash
git commit [options]
```


## Options

### `-m` or `--message`
- Adds a message to describe the commit:
```bash
git commit -m "Initial commit"
```

### `--amend`
- Edit the most recent commit message
```bash
git commit --amend
```
- An editor will open with the current commit message.
- Edit the message as desired, save, and close the editor.
