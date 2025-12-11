# How to Use the `git revert` Command

`git revert` is used to **undo a specific commit** by creating a **new commit** that reverses the changes of the original one.  
It does NOT rewrite commit history, making it safe for shared repositories.

---

# 1. Revert a Specific Commit
```bash
git revert <commit-hash>
````

**Usage:** Creates a new commit that undoes the changes of the specified commit.

---

# 2. Revert the Most Recent Commit

```bash
git revert HEAD
```

**Usage:** Reverts the latest commit safely without removing it from history.

---

# 3. Revert Multiple Commits

```bash
git revert <oldest-commit>..<newest-commit>
```

**Usage:** Reverts a range of commits in order.

---

# 4. Revert a Merge Commit

```bash
git revert -m 1 <merge-commit-hash>
```

**Usage:** Reverts a merge commit.
`-m 1` identifies which parent branch to keep (usually 1 = main).

---

# 5. Revert Without Opening Editor

```bash
git revert <commit-hash> --no-edit
```

**Usage:** Creates a revert commit without prompting for a commit message.

---

# 6. Cancel a Revert (Before finishing)

```bash
git revert --abort
```

**Usage:** Cancels the revert operation and restores the working state.

---

# Notes

* `git revert` is **safe** for public/shared repos (unlike `git reset`).
* It **does not delete history**; it adds a new commit that reverses old changes.
* Ideal for undoing a mistake after pushing.

---

# Summary of Key Commands

| Action                  | Command                        |
| ----------------------- | ------------------------------ |
| Revert a commit         | `git revert <hash>`            |
| Revert the last commit  | `git revert HEAD`              |
| Revert a merge commit   | `git revert -m 1 <merge-hash>` |
| Revert multiple commits | `git revert A..B`              |
| Revert without edit     | `git revert <hash> --no-edit`  |
| Cancel revert           | `git revert --abort`           |
