# How to Handle `Job Concurrency` in `GitHub Actions`?

GitHub Actions provides built-in concurrency controls to manage how workflows and jobs run in parallel. Concurrency helps prevent duplicate runs, reduce resource usage, and avoid race conditions—especially useful for deployments and long-running jobs.

---

## What Is Concurrency in GitHub Actions?

**Concurrency** allows you to control how many workflow runs or jobs can execute at the same time for a given group.  
When a new run starts in the same concurrency group, GitHub can either:
- Queue the new run, or
- Cancel the in-progress run

---

## Why Use Concurrency?

Concurrency is useful when you want to:

- Prevent multiple deployments at the same time
- Cancel outdated CI runs on new commits
- Avoid conflicts when accessing shared resources
- Save CI minutes and infrastructure costs

---

## Basic Workflow-Level Concurrency

You can define concurrency at the workflow level:

```yaml
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true
````

### What This Does

* Groups runs by workflow name and branch
* Cancels any in-progress run when a new one starts on the same branch

---

## Example: Cancel Previous Runs on New Commits

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]

concurrency:
  group: ci-${{ github.ref }}
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Running CI..."
```

This ensures only the **latest commit** is being built.

---

## Job-Level Concurrency

Concurrency can also be applied per job:

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    concurrency:
      group: deploy-production
      cancel-in-progress: false
    steps:
      - run: echo "Deploying to production..."
```

### When to Use Job-Level Concurrency

* Multiple jobs in the same workflow
* Only certain jobs (like deployment) must be serialized

---

## Environment-Based Concurrency (Best for Deployments)

GitHub environments automatically enforce concurrency.

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    environment: production
    steps:
      - run: echo "Deploying to production..."
```

### Benefits

* Only one job per environment runs at a time
* Supports required reviewers and secrets
* Ideal for production/staging deployments

---

## Using Branch-Based Concurrency

```yaml
concurrency:
  group: ${{ github.workflow }}-${{ github.ref_name }}
  cancel-in-progress: true
```

### Common Patterns

| Use Case        | Concurrency Group               |
| --------------- | ------------------------------- |
| Per branch      | `${{ github.ref }}`             |
| Per workflow    | `${{ github.workflow }}`        |
| Per environment | `deploy-${{ github.ref_name }}` |
| Global lock     | `global-lock`                   |

---

## Combining Concurrency with Manual Triggers

```yaml
on:
  push:
    branches: [ main ]
  workflow_dispatch:

concurrency:
  group: manual-and-push-${{ github.ref }}
  cancel-in-progress: false
```

This allows manual runs without canceling in-progress executions.

---

## Common Mistakes to Avoid

❌ Using a static group for all workflows
→ Causes unrelated workflows to block each other

❌ Forgetting `cancel-in-progress`
→ Leads to long queues instead of cancellation

❌ Applying concurrency too broadly
→ Reduces parallelism unnecessarily

---

## Best Practices

* Use **workflow-level concurrency** for CI pipelines
* Use **job-level or environment-based concurrency** for deployments
* Always include branch or environment info in the group name
* Enable cancellation for fast-feedback pipelines

---

## Example: CI + Deployment with Concurrency

```yaml
name: CI and Deploy

on:
  push:
    branches: [ main ]

concurrency:
  group: ci-${{ github.ref }}
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Building..."

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment: production
    steps:
      - run: echo "Deploying..."
```

---

## When NOT to Use Concurrency

* Jobs that must run for every commit (e.g., audits)
* Independent workflows with no shared state
* Data pipelines where each run is required

---

## Resources

* GitHub Actions Concurrency Docs: [https://docs.github.com/actions/using-jobs/using-concurrency](https://docs.github.com/actions/using-jobs/using-concurrency)
* GitHub Environments: [https://docs.github.com/actions/deployment/targeting-different-environments](https://docs.github.com/actions/deployment/targeting-different-environments)

---

Handle concurrency wisely and keep your pipelines fast and safe 🚦🚀

