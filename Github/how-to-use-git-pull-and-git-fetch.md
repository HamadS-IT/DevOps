# How to Use `git pull` and `git fetch`?

`git pull` and `git fetch` are both used to download updates from a remote repository, but they behave differently:

- **git fetch** → downloads changes *without applying them*
- **git pull** → downloads changes *and automatically merges them*

---

# 1. Git Fetch

`git fetch` downloads updates from the remote repository but does NOT modify your working directory or active branch.

## Fetch all updates from origin
```bash
git fetch
````

**Usage:**
Retrieves new commits, branches, and tags from the remote, but doesn't merge anything.

---

## Fetch updates from a specific branch

```bash
git fetch origin <branch-name>
```

**Usage:**
Downloads updates only for the given branch.

---

## Compare fetched updates with your branch

```bash
git diff <branch> origin/<branch>
```

**Usage:**
Shows what changed on the remote before you merge.

---

## View remote branches after fetching

```bash
git branch -r
```

**Usage:**
Lists remote-tracking branches fetched from the server.

---

# When to Use `git fetch`

* When you want to **review changes** before merging
* When you want to **stay synced** without modifying your local code
* When working in teams and you need to **inspect updates safely**

---

# 2. Git Pull

`git pull` does **two operations in one**:

1. `git fetch`
2. `git merge` (or `git rebase` if configured)

It fetches updates and automatically applies them to your current branch.

## Pull latest changes for current branch

```bash
git pull
```

**Usage:**
Downloads changes from the remote and merges them into your active branch.

---

## Pull from a specific remote branch

```bash
git pull origin <branch-name>
```

**Usage:**
Updates your local branch using changes from the specified remote branch.

---

## Pull using rebase instead of merge

```bash
git pull --rebase
```

**Usage:**
Fetches updates and rebases your work on top of the new commits for a cleaner history.

---

# When to Use `git pull`

* When you want your branch to **get the latest updates immediately**
* When you trust the remote changes and want them applied automatically
* When working solo or when your workflow requires frequent merges

---

# Key Differences Between Git Fetch and Git Pull

| Feature           | git fetch             | git pull                             |
| ----------------- | --------------------- | ------------------------------------ |
| Downloads updates | ✔️ Yes                | ✔️ Yes                               |
| Merges changes    | ❌ No                  | ✔️ Yes (auto-merge or rebase)        |
| Risk of conflicts | Low                   | Higher (merge happens automatically) |
| Safe to run       | Very safe             | Potential merge conflicts            |
| Use case          | Review before merging | Get updates instantly                |

---

# Summary of Commands

| Action                       | Command                     |
| ---------------------------- | --------------------------- |
| Fetch all updates            | `git fetch`                 |
| Fetch specific branch        | `git fetch origin <branch>` |
| Pull updates (fetch + merge) | `git pull`                  |
| Pull updates for a branch    | `git pull origin <branch>`  |
| Pull with rebase             | `git pull --rebase`         |

---

`git fetch` = *download only*
`git pull` = *download + merge*

