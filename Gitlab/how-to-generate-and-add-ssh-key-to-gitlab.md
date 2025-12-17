# How to `Generate` and `Add` an `SSH Key` to `GitLab`?

Using SSH keys with GitLab allows you to securely authenticate Git operations without entering your username and password each time. This guide walks you through generating an SSH key and adding it to your GitLab account.

---

## Why Use SSH with GitLab?

SSH keys provide:

- Secure authentication
- Password-less Git operations
- Better automation for CI/CD and servers
- Improved developer experience

---

## Prerequisites

Before you begin, ensure you have:

- A GitLab account
- Git installed on your machine
- Access to a terminal (Linux, macOS, or Windows)

---

## Step 1: Check for Existing SSH Keys

Check if you already have an SSH key:

```bash
ls -al ~/.ssh
````

Look for files such as:

* `id_ed25519` / `id_ed25519.pub`
* `id_rsa` / `id_rsa.pub`

If keys exist, you can reuse them or create a new one.

---

## Step 2: Generate a New SSH Key

### Recommended (ED25519)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Alternative (RSA – if ED25519 is not supported)

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

When prompted:

* Press **Enter** to accept the default file location
* Optionally set a passphrase for added security

---

## Step 3: Start the SSH Agent and Add the Key

### Linux / macOS

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

### Windows (Git Bash)

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

## Step 4: Copy the Public SSH Key

Copy your public key to the clipboard:

### macOS

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

### Linux

```bash
cat ~/.ssh/id_ed25519.pub
```

### Windows (Git Bash)

```bash
clip < ~/.ssh/id_ed25519.pub
```

---

## Step 5: Add the SSH Key to GitLab

1. Log in to GitLab
2. Click your **profile avatar** (top-right)
3. Go to **Preferences**
4. Select **SSH Keys**
5. Paste your public key into the **Key** field
6. Add:

   * **Title**: e.g., *Work Laptop*
   * **Expiration date** (optional but recommended)
7. Click **Add key**

---

## Step 6: Test the SSH Connection

Test your SSH connection to GitLab:

```bash
ssh -T git@gitlab.com
```

Successful output looks like:

```text
Welcome to GitLab, @username!
```

---

## Step 7: Use SSH with GitLab Repositories

### Clone a Repository Using SSH

```bash
git clone git@gitlab.com:username/project.git
```

### Update an Existing Repository to Use SSH

```bash
git remote set-url origin git@gitlab.com:username/project.git
```

---

## Common Issues & Fixes

### Permission denied (publickey)

* Ensure the SSH key is added to GitLab
* Check the SSH agent:

  ```bash
  ssh-add -l
  ```
* Verify which key is being used:

  ```bash
  ssh -vT git@gitlab.com
  ```

---

## Best Practices

* Use **ED25519** keys when possible
* Set a strong passphrase
* Use one SSH key per device
* Set expiration dates and rotate keys
* Remove unused keys from GitLab

---

## Use Cases

* Secure Git operations
* CI/CD pipelines
* Server access to GitLab repositories
* Infrastructure automation

---

## Resources

* GitLab SSH Documentation: [https://docs.gitlab.com/ee/user/ssh.html](https://docs.gitlab.com/ee/user/ssh.html)
* OpenSSH Manual: [https://man.openbsd.org/ssh](https://man.openbsd.org/ssh)

---

You’re now ready to use GitLab securely with SSH 🔐🚀

