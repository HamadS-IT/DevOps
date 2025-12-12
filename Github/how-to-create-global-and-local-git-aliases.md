# How to Create `Global` and `Local` `Git Aliases`?

Git aliases allow you to create shortcuts for long or frequently used Git commands.  
They help speed up your workflow and make Git easier and faster to use.

You can create **two types** of aliases:
- **Global aliases** → apply to every Git repository on your system
- **Local aliases** → apply only to a specific project

---

# 1. Creating Global Git Aliases

Use global aliases when you want the shortcut to work in **all Git repositories**.

## Create a global alias
```bash
git config --global alias.<shortname> "<git-command>"
````

### Examples

```bash
git config --global alias.st "status"
git config --global alias.cm "commit -m"
git config --global alias.br "branch"
git config --global alias.co "checkout"
git config --global alias.last "log -1 HEAD"
git config --global alias.unstage "restore --staged"
```

---

# 2. Creating Local Git Aliases

Use local aliases when the shortcut is needed **only for a specific project**.

## Create a local alias

```bash
git config alias.<shortname> "<git-command>"
```

### Examples

```bash
git config alias.lg "log --oneline --graph --decorate"
git config alias.df "diff"
git config alias.rb "rebase"
```

These aliases will work **only inside the current repository**.

---

# 3. Viewing Existing Aliases

### View global aliases

```bash
git config --global --get-regexp alias
```

### View local aliases

```bash
git config --get-regexp alias
```

---

# 4. Removing a Git Alias

### Remove a global alias

```bash
git config --global --unset alias.<shortname>
```

### Remove a local alias

```bash
git config --unset alias.<shortname>
```

---

# Summary of Commands

| Action              | Command Example                               |
| ------------------- | --------------------------------------------- |
| Create global alias | `git config --global alias.st "status"`       |
| Create local alias  | `git config alias.lg "log --oneline --graph"` |
| Show global aliases | `git config --global --get-regexp alias`      |
| Show local aliases  | `git config --get-regexp alias`               |
| Remove global alias | `git config --global --unset alias.st`        |
| Remove local alias  | `git config --unset alias.lg`                 |

---

Git aliases are extremely helpful shortcuts that improve speed, reduce typing, and create a smoother Git experience.
