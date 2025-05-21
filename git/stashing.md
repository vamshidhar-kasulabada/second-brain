# Git Stash Notes

## **What is Git Stash?**
- Git Stash temporarily saves changes in the working directory and staging area without committing them.
- Useful for switching branches or working on something else without losing progress.
- Stash uses a stack-like structure.

---

## **Key Commands**

### **1. Save Changes to the Stash**
```bash
git stash
```
- Stashes all uncommitted changes in the working directory and staging area.

### **2. Save Changes with a Message**
```bash
git stash push -m "description of changes"
```
- Adds a description for easier identification later.

### **3. List Stashes**
```bash
git stash list
```
- Shows all stashes in the stack, with their stash ID and description.

### **4. Apply the Latest Stash**
```bash
git stash apply
```
- Applies the most recent stash to the working directory without removing it from the stack.

### **5. Apply a Specific Stash**
```bash
git stash apply stash@{n}
```
- Applies a specific stash, where `n` is the stash ID.

### **6. Apply and Remove the Stash**
```bash
git stash pop
```
- Applies the latest stash and removes it from the stack.

### **7. Drop a Specific Stash**
```bash
git stash drop stash@{n}
```
- Deletes a specific stash.

### **8. Clear All Stashes**
```bash
git stash clear
```
- Removes all stashes from the stack.

### **9. Save Untracked or Ignored Files**
```bash
git stash -u  # Include untracked files
git stash -a  # Include untracked and ignored files
```

### **10. Show Stashed Changes**
```bash
git stash show
```
- Summary of changes in the latest stash.

For detailed changes:
```bash
git stash show -p
```

---
## Git Stash Push with Patch Option

### Overview

`git stash push -p` is a command used to stash selective changes in your working directory. The `-p` option stands for "patch" and allows you to interactively choose which changes to stash.

## Command Syntax

```bash
git stash push -p [-m "message"]
```

- **`-p`**: Initiates an interactive mode to selectively stash changes.
- **`-m "message"`**: Optional. Adds a descriptive message to your stash, helping you identify it later.

## How It Works

1. **Interactive Mode**: When you run `git stash push -p`, Git will present each change in your working directory one by one, allowing you to decide whether or not to stash it.

2. **Options During Interactive Stash**:
   - `y`: Stash this change.
   - `n`: Do not stash this change.
   - `q`: Quit, do not stash this change nor any of the remaining ones.
   - `a`: Stash this change and all remaining ones.
   - `d`: Do not stash this change nor any of the remaining ones.
   - `g`: Select a group of changes to stash.
   - `s`: Split the change into smaller parts.
   - `e`: Manually edit the change.
   - `?`: Help, display the help message.

3. **Adding a Message**: You can add a message to the stash for easier identification by using the `-m` option:

   ```bash
   git stash push -p -m "Descriptive message about the stash"
   ```

## Viewing Stashes

After stashing, you can view all your stashes with their messages using:

```bash
git stash list
```

## Example

```bash
git stash push -p -m "Stashing selective changes for feature X"
```

This command will interactively stash selected changes and associate them with the message "Stashing selective changes for feature X".

## Benefits

- **Selective Stashing**: Allows you to stash only specific changes, leaving others in your working directory.
- **Descriptive Messages**: Helps in organizing and identifying stashes with custom messages.

## Conclusion

`git stash push -p` is a powerful command for managing changes in a granular way, providing flexibility and clarity in your workflow.

---

## **Example Workflow**

1. **Start on a Feature Branch:**
   ```bash
   git switch feature/new-feature
   ```

2. **Make Some Changes Without Committing:**
   ```bash
   echo "Some changes" >> file.txt
   git add file.txt
   ```

3. **Stash the Changes:**
   ```bash
   git stash push -m "Work in progress on feature/new-feature"
   ```

4. **Switch to Another Branch:**
   ```bash
   git switch main
   ```

5. **Work on Another Task and Commit:**
   ```bash
   echo "Hotfix changes" >> hotfix.txt
   git add hotfix.txt
   git commit -m "Hotfix applied"
   ```

6. **Return to Your Feature Branch and Reapply Stash:**
   ```bash
   git switch feature/new-feature
   git stash apply
   ```

---

## **Advanced Usage**

### **Create a Branch from a Stash**
```bash
git stash branch <branch_name>
```
- Creates a new branch, applies the stash, and drops it from the stack.

### **Handle Stash Conflicts**
- Conflicts can occur if the stashed changes clash with current changes.
- Resolve conflicts, then:
  ```bash
  git add <resolved_files>
  git stash drop  # Remove the stash after resolving
  ```

---

## **Tips and Best Practices**
- **Use Stash Descriptions:** Always add a description to identify stashes easily.
- **Stash Before Switching Branches:** Prevents mixing changes when switching contexts.
- **Avoid Overusing Stashes:** For prolonged work, commit changes to a work-in-progress (WIP) branch instead.
