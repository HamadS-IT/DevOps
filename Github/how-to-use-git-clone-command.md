# How to Use the `git clone` Command?

The `git clone` command is used to **download an existing Git repository** from a remote server (like GitHub, GitLab, Bitbucket) to your local machine.  
It creates a full copy of the repository—including branches, commit history, and files.

---

# 1. Clone a Repository (HTTPS)

```bash
git clone https://github.com/user/repo.git
````

**Usage:**
Downloads the repository using HTTPS.
Most commonly used and requires username/token when pushing.

---

# 2. Clone a Repository (SSH)

```bash
git clone git@github.com:user/repo.git
```

**Usage:**
Uses SSH keys for authentication.
Recommended for developers who push often because it avoids entering tokens.

---

# 3. Clone a Repository Into a Specific Folder

```bash
git clone https://github.com/user/repo.git my-folder
```

**Usage:**
Clones the repository into a folder named `my-folder` instead of the default repo name.

---

# 4. Clone Only One Branch

```bash
git clone --branch <branch-name> https://github.com/user/repo.git
```

**Usage:**
Downloads only the specified branch instead of the whole repository.

---

# 5. Clone Without Full History (Shallow Clone)

```bash
git clone --depth 1 https://github.com/user/repo.git
```

**Usage:**
Downloads the latest snapshot only (no commit history).
Useful for large repositories.

---

# 6. Clone With Specific Depth

```bash
git clone --depth <number> https://github.com/user/repo.git
```

**Usage:**
Downloads only the latest N commits.

---

# 7. Clone a Bare Repository

```bash
git clone --bare https://github.com/user/repo.git
```

**Usage:**
Creates a **bare repository** (no working directory), often used for servers or mirrors.

---

# 8. Clone a Mirror Repository

```bash
git clone --mirror https://github.com/user/repo.git
```

**Usage:**
Creates a full mirror including refs, branches, and hooks.
Used for backups or repository migrations.

---

# Summary of Commands

| Action                             | Command Example                              |
| ---------------------------------- | -------------------------------------------- |
| Clone repo (HTTPS)                 | `git clone https://github.com/user/repo.git` |
| Clone repo (SSH)                   | `git clone git@github.com:user/repo.git`     |
| Clone into specific folder         | `git clone <url> my-folder`                  |
| Clone single branch                | `git clone --branch <branch> <url>`          |
| Shallow clone (latest commit only) | `git clone --depth 1 <url>`                  |
| Clone with custom depth            | `git clone --depth 10 <url>`                 |
| Create bare repository             | `git clone --bare <url>`                     |
| Create mirror repository           | `git clone --mirror <url>`                   |

---

`git clone` is usually the first command used when starting work on an existing repository.

