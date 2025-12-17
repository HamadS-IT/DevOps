# How to `Automate` the `Angular Build Process` Using `GitHub Actions`?

Automating the Angular build process with GitHub Actions helps ensure consistent builds, catch errors early, and prepare your app for deployment. This guide shows how to set up a CI workflow that installs dependencies and builds an Angular application automatically.

---

## Prerequisites

Before you begin, make sure you have:

- An Angular project stored in a GitHub repository
- Node.js and npm configured in your project
- Basic knowledge of Angular and GitHub Actions

---

## Step 1: Create the Workflow Directory

If it doesn’t already exist, create the following directory in your repository:

```

.github/workflows

```

---

## Step 2: Create the Workflow File

Create a new file named:

```

angular-build.yml

````

---

## Step 3: Define the GitHub Actions Workflow

Add the following content to `angular-build.yml`:

```yaml
name: Angular Build CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Build Angular app
        run: npm run build
````

---

## Step 4: Understand the Workflow

### Checkout Code

```yaml
uses: actions/checkout@v4
```

Fetches your repository code into the runner.

### Set Up Node.js

```yaml
uses: actions/setup-node@v4
```

Installs Node.js and enables dependency caching for faster builds.

### Install Dependencies

```yaml
npm ci
```

Installs dependencies using the lock file for consistent builds.

### Build the App

```yaml
npm run build
```

Runs the Angular production build (usually mapped to `ng build`).

---

## Step 5: Optional – Specify Production Configuration

If your project uses Angular environments:

```yaml
- name: Build Angular app (production)
  run: npm run build -- --configuration=production
```

---

## Step 6: Commit and Push

Commit and push the workflow file:

```bash
git add .github/workflows/angular-build.yml
git commit -m "Automate Angular build with GitHub Actions"
git push origin main
```

---

## Step 7: View the Build Results

1. Go to your GitHub repository
2. Click the **Actions** tab
3. Select **Angular Build CI**
4. Review logs and build output

---

## Optional Enhancements

### Add Unit Tests

```yaml
- name: Run unit tests
  run: npm test -- --watch=false --browsers=ChromeHeadless
```

### Upload Build Artifacts

```yaml
- name: Upload build artifacts
  uses: actions/upload-artifact@v4
  with:
    name: angular-dist
    path: dist/
```

### Cache Angular CLI

Already handled via `cache: 'npm'` in `setup-node`.

---

## Common Issues & Tips

* Ensure `package-lock.json` is committed
* Match Node.js version with your local environment
* Angular builds can fail due to missing environment variables
* Use `npm ci` instead of `npm install` for CI

---

## Example Use Cases

* Continuous Integration (CI)
* Pre-deployment validation
* Pull request checks
* Automated quality gates

---

## Resources

* Angular CLI Documentation: [https://angular.io/cli](https://angular.io/cli)
* GitHub Actions Documentation: [https://docs.github.com/actions](https://docs.github.com/actions)
* Node.js Setup Action: [https://github.com/actions/setup-node](https://github.com/actions/setup-node)

---

Happy building with Angular and GitHub Actions! 🚀

