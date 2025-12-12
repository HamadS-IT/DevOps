# How to Use the `git commit --amend` Command?

`git commit --amend` allows you to **modify the most recent commit**.  
You can use it to fix commit messages, add files you forgot to include, or adjust the latest commit without creating a new one.

---

# 1. Amend the Last Commit Message

```bash
git commit --amend
````

**Usage:**
Opens your editor so you can rewrite the message of the latest commit without changing its content.

---

# 2. Amend Commit Message Without Opening Editor

```bash
git commit --amend -m "New commit message"
```

**Usage:**
Replaces the previous commit message directly using the `-m` flag.

---

# 3. Add Missing Files to the Last Commit

```bash
git add <file>
git commit --amend --no-edit
```

**Usage:**
Stages new files or changes and adds them to the previous commit **without changing the message**.

---

# 4. Replace Last Commit With All New Changes

```bash
git add .
git commit --amend
```

**Usage:**
Useful when you want the latest commit to fully represent your most recent work.

---

# 5. Amend the Last Commit After Pushing (Use With Caution)

```bash
git commit --amend
git push --force
```

**Usage:**
Rewrites history and requires a force push.
⚠️ Avoid doing this on shared branches to prevent conflicts for other developers.

---

# Important Notes

* `git amend` **rewrites history** → only safe before pushing.
* Use `--no-edit` to keep the same message while updating content.
* After amending a pushed commit, you must use `git push --force`.
* Ideal for fixing small mistakes in the most recent commit.

---

# Summary of Commands

| Action                           | Command                                           |
| -------------------------------- | ------------------------------------------------- |
| Edit last commit message         | `git commit --amend`                              |
| Replace message without editor   | `git commit --amend -m "New message"`             |
| Add missing files to last commit | `git add <file>` + `git commit --amend --no-edit` |
| Overwrite last commit content    | `git add .` + `git commit --amend`                |
| Amend after push (dangerous)     | `git push --force`                                |
