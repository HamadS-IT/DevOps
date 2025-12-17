# How to `Schedule GitHub Actions Workflows`?

GitHub Actions allows you to automatically run workflows on a schedule using cron syntax. This is useful for tasks like running nightly tests, generating reports, cleaning up resources, or syncing data.

---

## What Is a Scheduled Workflow?

A **scheduled workflow** runs automatically at specific times using the `schedule` event.  
Schedules are defined using **cron expressions** inside your workflow YAML file.

---

## Prerequisites

Before you begin, ensure you have:

- A GitHub repository
- Basic understanding of GitHub Actions
- Familiarity with YAML files

---

## Step 1: Create or Open a Workflow File

Scheduled workflows must be stored in:

```

.github/workflows/

```

Create a new file, for example:

```

scheduled-job.yml

````

---

## Step 2: Add a Schedule Trigger

Below is a simple workflow that runs every day at midnight (UTC):

```yaml
name: Scheduled Workflow Example

on:
  schedule:
    - cron: "0 0 * * *"

jobs:
  scheduled-job:
    runs-on: ubuntu-latest

    steps:
      - name: Print current date
        run: date
````

---

## Step 3: Understand Cron Syntax

Cron expressions use five fields:

```
┌──────── minute (0 - 59)
│ ┌──────── hour (0 - 23)
│ │ ┌──────── day of month (1 - 31)
│ │ │ ┌──────── month (1 - 12)
│ │ │ │ ┌──────── day of week (0 - 6, Sunday = 0)
│ │ │ │ │
│ │ │ │ │
* * * * *
```

### Common Examples

| Schedule                 | Cron Expression |
| ------------------------ | --------------- |
| Every day at midnight    | `0 0 * * *`     |
| Every hour               | `0 * * * *`     |
| Every Monday at 9 AM     | `0 9 * * 1`     |
| Every 15 minutes         | `*/15 * * * *`  |
| First day of every month | `0 0 1 * *`     |

⚠️ **Important:** GitHub Actions schedules run in **UTC time**.

---

## Step 4: Combine Schedule with Other Triggers

You can run a workflow both manually and on a schedule:

```yaml
on:
  schedule:
    - cron: "0 2 * * *"
  workflow_dispatch:
```

This allows you to:

* Run automatically on a schedule
* Trigger manually from the GitHub UI

---

## Step 5: Commit and Push

Commit your workflow file:

```bash
git add .github/workflows/scheduled-job.yml
git commit -m "Add scheduled GitHub Actions workflow"
git push origin main
```

---

## Step 6: Verify the Workflow

1. Go to your repository on GitHub
2. Open the **Actions** tab
3. Select your scheduled workflow
4. Wait for the scheduled time or trigger it manually

GitHub may delay scheduled jobs slightly depending on system load.

---

## Important Notes & Limitations

* Scheduled workflows **only run on the default branch**
* Cron schedules are evaluated in **UTC**
* Workflows may not run if the repository is inactive for long periods
* Minimum interval is **5 minutes**

---

## Common Use Cases

* Nightly test runs
* Dependency updates
* Database cleanup jobs
* Generating reports
* Health checks

---

## Resources

* GitHub Actions Schedule Events: [https://docs.github.com/actions/using-workflows/events-that-trigger-workflows#schedule](https://docs.github.com/actions/using-workflows/events-that-trigger-workflows#schedule)
* Cron Expression Generator: [https://crontab.guru](https://crontab.guru)

---

Happy scheduling! ⏰🚀
