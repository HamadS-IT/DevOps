# How to Use the `git reset` Command ?

`git reset` is a powerful Git command used to **undo commits**, **unstage files**, or **reset the working directory**.  
Unlike `git revert`, `git reset` **can rewrite history**, so it should be used with caution—especially in shared repos.

---

# Types of Git Reset

Git reset has **three modes**, each affecting different parts of your project:

| Mode        | Affects Staging Area | Affects Working Directory | Rewrites History |
|-------------|------------------------|----------------------------|-------------------|
| `--soft`    | ✔️ Yes                 | ❌ No                      | ✔️ Yes            |
| `--mixed`   | ✔️ Yes                 | ✔️ Partial (unstages)      | ✔️ Yes            |
| `--hard`    | ✔️ Yes                 | ✔️ Yes                     | ✔️ Yes            |

---

# 1. Soft Reset (keeps changes staged)
```bash
git reset --soft <commit-hash>
````

**Usage:**
Moves HEAD to a previous commit but keeps all your changes **staged**.
Useful when you want to redo recent commits.

---

# 2. Mixed Reset (default, unstages changes)

```bash
git reset <commit-hash>
```

or explicitly:

```bash
git reset --mixed <commit-hash>
```

**Usage:**
Moves HEAD back and **unstages** changes, but keeps your working directory unchanged.

---

# 3. Hard Reset (dangerous, deletes changes)

```bash
git reset --hard <commit-hash>
```

**Usage:**
Moves HEAD back and **erases all changes** in staging and working directory.
⚠️ Use with caution! Lost work cannot be recovered.

---

# 4. Unstage a File (without losing changes)

```bash
git reset <file>
```

**Usage:**
Removes the file from staging while keeping your local changes.

---

# 5. Reset to the Previous Commit

```bash
git reset --hard HEAD~1
```

**Usage:**
Removes the most recent commit and all changes in it.

---

# 6. Reset to Remote Branch State (force sync)

```bash
git reset --hard origin/main
```

**Usage:**
Replaces local changes to match the remote branch exactly.

---

# 7. Keep Changes but Uncommit the Last Commit

```bash
git reset --soft HEAD~1
```

**Usage:**
Removes the latest commit but keeps the changes staged.

---

# Important Notes

* `git reset --hard` **permanently deletes uncommitted work**
* `git reset` can rewrite history → **don’t use on shared branches**
* Use `git revert` instead if you need a safe undo after pushing

---

# Summary of Commands

| Action                            | Command                        |
| --------------------------------- | ------------------------------ |
| Soft reset (keep changes staged)  | `git reset --soft <hash>`      |
| Mixed reset (unstage changes)     | `git reset <hash>`             |
| Hard reset (delete changes)       | `git reset --hard <hash>`      |
| Unstage a file                    | `git reset <file>`             |
| Undo last commit but keep changes | `git reset --soft HEAD~1`      |
| Hard reset to remote state        | `git reset --hard origin/main` |

