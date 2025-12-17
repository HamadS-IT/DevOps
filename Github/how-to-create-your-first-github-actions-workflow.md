# How to Create Your First `GitHub Actions Workflow`?

GitHub Actions allows you to automate tasks such as testing, building, and deploying your code directly from your GitHub repository. This guide walks you through creating your first workflow step by step.

---

## What Is a GitHub Actions Workflow?

A **workflow** is an automated process made up of one or more **jobs**.  
Workflows are defined using YAML files and stored in the `.github/workflows` directory of your repository.

---

## Prerequisites

Before you begin, make sure you have:

- A GitHub account
- A GitHub repository
- Basic knowledge of Git and GitHub

---

## Step 1: Create the Workflow Directory

In your repository, create the following directory if it doesn’t already exist:

```

.github/workflows

```

GitHub automatically detects workflows placed in this folder.

---

## Step 2: Create a Workflow File

Inside `.github/workflows`, create a file named:

```

hello-world.yml

````

The file name can be anything, but it must end with `.yml` or `.yaml`.

---

## Step 3: Define a Simple Workflow

Add the following content to `hello-world.yml`:

```yaml
name: Hello World Workflow

on:
  push:
    branches:
      - main

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - name: Print a message
        run: echo "Hello, GitHub Actions!"
````

---

## Step 4: Understand the Workflow

### `name`

The name of the workflow as it appears in the GitHub Actions UI.

### `on`

Defines the event that triggers the workflow.
In this example, it runs on every push to the `main` branch.

### `jobs`

A workflow can have one or more jobs.

### `runs-on`

Specifies the virtual machine to run the job on.

### `steps`

A sequence of tasks executed as part of the job.

---

## Step 5: Commit and Push

Commit the file and push it to your repository:

```bash
git add .github/workflows/hello-world.yml
git commit -m "Add first GitHub Actions workflow"
git push origin main
```

---

## Step 6: View the Workflow Run

1. Go to your GitHub repository
2. Click the **Actions** tab
3. Select **Hello World Workflow**
4. Click on the latest run to see logs and output

You should see:

```
Hello, GitHub Actions!
```

---

## Next Steps

Once you’re comfortable with the basics, try:

* Running workflows on pull requests
* Adding steps for testing or linting
* Using official GitHub Actions from the Marketplace
* Setting up CI/CD pipelines

---

## Resources

* GitHub Actions Documentation: [https://docs.github.com/actions](https://docs.github.com/actions)
* GitHub Actions Marketplace: [https://github.com/marketplace?type=actions](https://github.com/marketplace?type=actions)

---

Happy automating! 🚀

