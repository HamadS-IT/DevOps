# What Are `GitLab Runners`?

GitLab Runners are the agents that run jobs in GitLab CI/CD pipelines. They take the code from your repository, execute the defined pipeline jobs, and report the results back to GitLab.

---

## What Is a GitLab Runner?

A **GitLab Runner** is an application that processes jobs from GitLab CI/CD. It executes scripts defined in the `.gitlab-ci.yml` file and can run on different environments:

- Your local machine
- Virtual machines
- Docker containers
- Cloud infrastructure

---

## Key Features of GitLab Runners

- Executes CI/CD jobs defined in `.gitlab-ci.yml`
- Supports multiple executors (Shell, Docker, Kubernetes, etc.)
- Can be shared or dedicated per project
- Runs jobs in isolation
- Supports caching and artifacts
- Auto-scalable in GitLab Runner Manager (for cloud setups)

---

## Types of GitLab Runners

### 1. Shared Runners
- Provided by GitLab for public projects
- Available to all projects in a GitLab instance
- Useful for small teams or open-source projects

### 2. Specific (Project) Runners
- Dedicated to a single project or group
- Can have specialized configurations
- Recommended for private or large projects

---

## How GitLab Runners Work

1. **Pipeline triggers**: A Git push, merge request, or schedule triggers a pipeline.
2. **Job assignment**: GitLab assigns jobs to available runners.
3. **Job execution**: Runner executes the job according to `.gitlab-ci.yml`.
4. **Report back**: Runner sends logs, success/failure status, and artifacts back to GitLab.

---

## Executors in GitLab Runners

GitLab Runners support different **executors** which define the environment used to run jobs:

| Executor | Description |
|----------|------------|
| Shell    | Runs jobs in the host machine shell |
| Docker   | Runs jobs inside Docker containers |
| Docker+Machine | Dynamic Docker runner with auto-scaling |
| Kubernetes | Runs jobs inside Kubernetes pods |
| Custom   | Use a custom executor script |

---

## Benefits of GitLab Runners

- Automation: Jobs run automatically on code changes
- Isolation: Jobs run in separate environments
- Scalability: Supports multiple runners for parallel jobs
- Flexibility: Supports different languages, OS, and tools
- CI/CD Integration: Fully integrated with GitLab pipelines

---

## Example: Using a GitLab Runner in `.gitlab-ci.yml`

```yaml
stages:
  - build
  - test

build_job:
  stage: build
  script:
    - echo "Building the project..."
  tags:
    - my-runner

test_job:
  stage: test
  script:
    - echo "Running tests..."
  tags:
    - my-runner
````

> **Note**: The `tags` field specifies which runner(s) can pick up the job.

---

## Registering a GitLab Runner

1. Install GitLab Runner on your machine or server
2. Run the registration command:

```bash
gitlab-runner register
```

3. Provide:

* GitLab instance URL
* Registration token (from GitLab project or group)
* Description
* Tags (optional)
* Executor type

4. Runner is now active and ready to execute jobs

---

## Best Practices

* Use shared runners for small or public projects
* Use specific runners for sensitive or resource-intensive jobs
* Tag runners to match job requirements
* Enable caching and artifacts to speed up pipelines
* Monitor runner usage and health

---

## Resources

* GitLab Runner Documentation: [https://docs.gitlab.com/runner/](https://docs.gitlab.com/runner/)
* GitLab CI/CD Pipelines: [https://docs.gitlab.com/ee/ci/](https://docs.gitlab.com/ee/ci/)
* Install GitLab Runner: [https://docs.gitlab.com/runner/install/](https://docs.gitlab.com/runner/install/)

---

GitLab Runners are the backbone of automation in GitLab CI/CD, enabling fast, consistent, and isolated execution of jobs 🚀
