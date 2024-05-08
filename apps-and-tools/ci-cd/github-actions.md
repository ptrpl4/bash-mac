# ↗️ GitHub actions

## Components

- **Events** - initiate or trigger an execution of a GitHub action workflow. An event may be an internal GitHub event (such as a push, a release, fork, issues, or a pull request), a scheduled event (triggered at a specific time, like a cron job), or an arbitrary external event (triggered by a webhook call to the GitHub API).
- **Workflows** - are composed of jobs that can be started by an event or by scheduling them to run at a specific time. Workflows assist in building, testing, releasing, or deploying project to GitHub.
- **Job** - a set of steps that run inside the same virtual machine runner, or inside a container. By default, they are executed in parallel, in other words, they don't wait for the previous job to be finished. Moreover, we can configure the jobs to run one after another if needed.
- **Actions** - specified actions for solving particular problems.
- **Runners** - is a virtual machine that runs a job. The runner is responsible for looking for the available jobs, then executes each job at a time. After the job is finished running, the runner reports the progress and logs of the job to GitHub. The runners hosted by GitHub consist of Ubuntu, Linux, Windows, and macOS.

## Workflow syntax

`.github/workflows`

```yaml
# your-repo-name/.github/workflows/first_workflow.yml

name: First Workflow    # name of the workflow
                                         
on: push   # on - specifies when the workflow will be executed
                                               
jobs:
                         
  first-job:                           
    name: Name of first step                    
    runs-on: ubuntu-latest # specifies the virtual environment
    steps:

      #step 1                           
      - name: Print a greeting  # Each step is preceded by `-`
        run: echo Hi from our first workflow! # All the steps are executed sequentially.

      #step 2 
      - uses: actions/checkout@v2.3.4    # v 2.3.4 of the checkout package should be used
  second-job:
    strategy:
      matrix:
        runtimes: [10, 12, 14]
        os_version: [ubuntu-latest, windows-latest]
    runs-on: ${{ matrix.os_version}}
    steps:
      - uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.version }}
```