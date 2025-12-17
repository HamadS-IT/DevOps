# How to `Create` and `Merge` `Branches` in `GitLab`?

Branches in GitLab allow developers to work on features, bug fixes, or experiments without affecting the main codebase. This guide explains how to create branches and merge them using both the GitLab UI and the command line.

---

## What Is a Branch?

A **branch** is an independent line of development in a Git repository.  
The default branch is usually called `main` or `master`.

---

## Why Use Branches?

Branches help you:

- Develop features in isolation
- Fix bugs without affecting production code
- Collaborate safely with team members
- Maintain a clean and stable main branch

---

## Prerequisites

Before you begin, make sure you have:

- A GitLab account
- A GitLab repository
- Git installed on your machine

---

## Method 1: Create a Branch Using the GitLab UI

### Step 1: Open Your Repository

1. Log in to GitLab
2. Open your project
3. Go to **Code → Branches**

---

### Step 2: Create a New Branch

1. Click **New branch**
2. Enter:
   - **Branch name** (e.g., `feature/login-page`)
   - **Create from**: `main`
3. Click **Create branch**

Your new branch is now available.

---

## Method 2: Create a Branch Using the Command Line

### Step 1: Clone the Repository (If Needed)

```bash
git clone git@gitlab.com:username/project.git
cd project
````

---

### Step 2: Create and Switch to a New Branch

```bash
git checkout -b feature/login-page
```

Or using the newer syntax:

```bash
git switch -c feature/login-page
```

---

### Step 3: Push the Branch to GitLab

```bash
git push -u origin feature/login-page
```

---

## Making Changes and Committing

After making changes:

```bash
git add .
git commit -m "Add login page feature"
git push
```

---

## Merging Branches Using Merge Requests (Recommended)

### Step 1: Create a Merge Request (MR)

1. Go to your project in GitLab
2. Click **Merge requests**
3. Click **New merge request**
4. Select:

   * **Source branch**: `feature/login-page`
   * **Target branch**: `main`
5. Click **Compare branches and continue**

---

### Step 2: Review and Approve

* Add a title and description
* Assign reviewers
* Resolve comments if any
* Ensure pipelines pass

---

### Step 3: Merge the Branch

Click **Merge** once approvals and checks are complete.

---

## Merging via Command Line (Not Recommended for Teams)

```bash
git checkout main
git pull origin main
git merge feature/login-page
git push origin main
```

⚠️ Merge requests are preferred because they provide:

* Code reviews
* CI/CD checks
* Approval workflows

---

## Deleting a Branch After Merge

### From GitLab UI

* GitLab prompts you to delete the source branch after merging

### From Command Line

```bash
git branch -d feature/login-page
git push origin --delete feature/login-page
```

---

## Handling Merge Conflicts

If conflicts occur:

```bash
git checkout feature/login-page
git pull origin main
```

Resolve conflicts, then:

```bash
git add .
git commit
git push
```

Update the merge request and merge again.

---

## Best Practices

* Use descriptive branch names (`feature/`, `bugfix/`, `hotfix/`)
* Keep branches small and focused
* Always use merge requests
* Protect the `main` branch
* Delete merged branches

---

## Common Branching Strategies

| Strategy          | Description                   |
| ----------------- | ----------------------------- |
| Feature branching | One branch per feature        |
| Git Flow          | Structured release management |
| Trunk-based       | Short-lived branches          |

---

## Resources

* GitLab Branches Documentation: [https://docs.gitlab.com/ee/user/project/repository/branches/](https://docs.gitlab.com/ee/user/project/repository/branches/)
* GitLab Merge Requests: [https://docs.gitlab.com/ee/user/project/merge_requests/](https://docs.gitlab.com/ee/user/project/merge_requests/)
* Git Documentation: [https://git-scm.com/docs](https://git-scm.com/docs)

---

You’re now ready to create and merge branches in GitLab with confidence 🌿🚀

