# ActionInAction

[![My First Workflow](https://github.com/Nawwalicious/ActionInAction/actions/workflows/MyFirstWorkflow.yml/badge.svg)](https://github.com/Nawwalicious/ActionInAction/actions/workflows/MyFirstWorkflow.yml)

My first **GitHub Actions** workflow, built for **CP5401 - Software Quality Engineering, Prac 1**.

The repo is intentionally small. Its job is to show the full loop of a CI workflow: write a YAML file, push it, and watch GitHub run it automatically.

## What the workflow does

| | |
|---|---|
| **Workflow name** | My First Workflow |
| **File** | [`.github/workflows/MyFirstWorkflow.yml`](.github/workflows/MyFirstWorkflow.yml) |
| **Triggers** | A push to the `main` branch, or a manual run (`workflow_dispatch`) |
| **Job** | `MyFirstJob` |
| **Runner** | `ubuntu-latest` (GitHub-hosted Linux machine) |
| **Steps** | 1. Check out the repository 2. Print `Hello World! Nawwal Here` to the console |

```yaml
name: My First Workflow

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  MyFirstJob:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - run: echo "Hello World!"
```

## How to run it

- **Automatically:** push any commit to `main`. The workflow starts on its own.
- **Manually:** go to the **Actions** tab, choose **My First Workflow**, then click **Run workflow**.

To see the result, open the **Actions** tab, click the latest run, open `MyFirstJob`, and expand the step that prints `Hello World!`.

## Key concepts

- **Workflow:** an automated process defined in a YAML file under `.github/workflows/`.
- **Trigger:** the event that starts a workflow, such as a push or a manual dispatch.
- **Job:** a group of steps that runs on one runner. Jobs run in parallel by default.
- **Runner:** the machine that executes a job. GitHub provides Linux, macOS and Windows runners.
- **Step:** a single task in a job, either a shell command (`run`) or a reusable action (`uses`).
- **Action:** a reusable, shareable step, for example `actions/checkout`.

## Why this matters for software quality

Continuous Integration (CI) runs automated checks every time code changes. Catching problems early, on every commit and without relying on someone remembering to test, is one of the ways teams prevent software errors from becoming faults and failures in production. This workflow only prints a message, but the same structure can run builds, tests and linters.

## Repository structure

```
ActionInAction/
├── .github/
│   └── workflows/
│       └── MyFirstWorkflow.yml
└── README.md
```

## Author

Nawwal Ahmed, CP5401 Software Quality Engineering.
