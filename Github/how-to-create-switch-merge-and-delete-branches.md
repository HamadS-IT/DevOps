# How to `Create`, `Switch`, `Merge`, and `Delete` `Git Branches`?

Git branches allow you to work on features, fixes, or experiments without affecting the main project.  
Below are the essential commands for working with branches.

---

# 1. Create a Branch

```bash
git branch <branch-name>
````

**Usage:** Creates a new branch but does not switch to it.

### Create and switch in one command

```bash
git switch -c <branch-name>
```

**Usage:** Creates a new branch and switches to it immediately.

---

# 2. Switch Between Branches

```bash
git switch <branch-name>
```

**Usage:** Moves you to the specified branch.

### Switch to the main branch

```bash
git switch main
```

---

# 3. List Branches

```bash
git branch
```

**Usage:** Shows all local branches.

### List remote branches

```bash
git branch -r
```

---

# 4. Merge a Branch

```bash
git merge <branch-name>
```

**Usage:** Merges the specified branch into the current branch.

### Example workflow

Switch to the branch you want to merge *into*:

```bash
git switch main
git merge feature-branch
```

---

# 5. Delete a Branch (Locally)

### Safe delete (only deletes if fully merged)

```bash
git branch -d <branch-name>
```

### Force delete (dangerous)

```bash
git branch -D <branch-name>
```

**Usage:** Deletes the local branch.
Use force delete only when you are sure you no longer need the branch.

---

# 6. Delete a Branch (Remote)

```bash
git push origin --delete <branch-name>
```

**Usage:** Removes the branch from the remote repository (e.g., GitHub).

---

# Summary of Commands

| Action                      | Command                           |
| --------------------------- | --------------------------------- |
| Create branch               | `git branch <name>`               |
| Create + switch             | `git switch -c <name>`            |
| Switch branch               | `git switch <name>`               |
| List branches               | `git branch`                      |
| Merge branch                | `git merge <name>`                |
| Delete local branch (safe)  | `git branch -d <name>`            |
| Delete local branch (force) | `git branch -D <name>`            |
| Delete remote branch        | `git push origin --delete <name>` |

---

These branch commands form the core of everyday Git workflows for feature development, bug fixes, and code management.
