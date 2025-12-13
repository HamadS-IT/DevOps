# How to Use the `git stash` Command?

The `git stash` command temporarily saves changes in your working directory so you can switch branches or work on something else without committing incomplete work.

---

## Basic Usage

### Stash Current Changes

Stashes all **tracked** modified files.

```bash
git stash
````

Equivalent to:

```bash
git stash push
```

---

### Stash With a Message

```bash
git stash push -m "WIP: login feature"
```

---

## View Stashed Changes

### List All Stashes

```bash
git stash list
```

Example output:

```text
stash@{0}: On main: WIP: login feature
stash@{1}: On main: fix navbar
```

---

### Show Stash Details

```bash
git stash show
```

Show full diff:

```bash
git stash show -p
```

---

## Apply Stashed Changes

### Apply the Latest Stash

```bash
git stash apply
```

---

### Apply a Specific Stash

```bash
git stash apply stash@{1}
```

---

### Apply and Remove Stash

```bash
git stash pop
```

> `pop` applies the stash and deletes it if successful.

---

## Stash Untracked and Ignored Files

### Include Untracked Files

```bash
git stash -u
```

or

```bash
git stash --include-untracked
```

---

### Include Ignored Files

```bash
git stash -a
```

or

```bash
git stash --all
```

---

## Stash Specific Files

```bash
git stash push file1.js file2.css
```

---

## Create a Branch From a Stash

```bash
git stash branch new-branch stash@{0}
```

This:

* Creates a new branch
* Applies the stash
* Drops the stash if successful

---

## Remove Stashes

### Drop a Specific Stash

```bash
git stash drop stash@{1}
```

---

### Clear All Stashes

```bash
git stash clear
```

⚠️ This action cannot be undone.

---

## Common Use Cases

* Switching branches quickly
* Saving unfinished work
* Pulling updates without committing
* Handling merge conflicts

---

## Example Workflow

```bash
git status
git stash push -m "WIP: checkout page"
git checkout main
git pull
git checkout feature
git stash pop
```

---

## Tips & Best Practices

* Always use messages for clarity
* Clear old stashes regularly
* Avoid using stash as long-term storage
* Commit instead when possible

---

## Common Issues

### Merge Conflicts After Applying Stash

Resolve conflicts manually, then:

```bash
git add .
git commit -m "Resolve stash conflicts"
```

---

## Conclusion

`git stash` is a powerful tool for managing unfinished work without polluting your commit history.

Happy stashing 🚀