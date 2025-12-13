# How to Use the `git diff` Command?

The `git diff` command shows differences between files, commits, branches, or working directory states in Git. It is commonly used to review changes before committing.

---

## Basic Usage

### Show Unstaged Changes

Displays changes in the working directory that are **not staged**.

```bash
git diff
````

---

### Show Staged Changes

Shows changes that have been added to the staging area.

```bash
git diff --staged
```

or

```bash
git diff --cached
```

---

## Compare Files

### Compare a File With the Last Commit

```bash
git diff HEAD index.html
```

---

### Compare Two Files

```bash
git diff file1.js file2.js
```

---

## Compare Commits

### Compare Two Commits

```bash
git diff commit1 commit2
```

Example:

```bash
git diff a1b2c3d e4f5g6h
```

---

### Compare Current Branch With Another Branch

```bash
git diff main feature-branch
```

---

## Compare With Previous Commit

```bash
git diff HEAD~1
```

---

## Compare Specific Changes

### Word-Level Diff

Highlights word-by-word changes instead of lines.

```bash
git diff --word-diff
```

---

### Show Only File Names Changed

```bash
git diff --name-only
```

---

### Show Summary of Changes

```bash
git diff --stat
```

---

## Ignore Whitespace Changes

```bash
git diff -w
```

---

## Diff a Specific Commit

```bash
git diff <commit-hash>^ <commit-hash>
```

---

## Colorized Output (Default)

Git highlights changes:

* **Red**: removed lines
* **Green**: added lines

To force color:

```bash
git diff --color
```

---

## Redirect Diff Output to a File

```bash
git diff > changes.diff
```

---

## View Diff in External Tool

```bash
git difftool
```

---

## Common Use Cases

* Review changes before committing
* Compare branches before merging
* Identify accidental changes
* Debug unexpected behavior

---

## Example Workflow

```bash
git status
git diff
git add .
git diff --staged
git commit -m "Update feature"
```

---

## Tips & Best Practices

* Run `git diff` before every commit
* Use `--stat` for quick overviews
* Combine with `less` for large diffs:

  ```bash
  git diff | less
  ```

---

## Conclusion

`git diff` is a powerful tool for understanding code changes and maintaining clean version control history.

Happy coding 🚀

