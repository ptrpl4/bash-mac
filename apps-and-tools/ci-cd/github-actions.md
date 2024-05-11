# ↗️ GitHub actions

links:
- https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions#understanding-the-workflow-file

## Components

- **Workflows** - are composed of jobs that can be started by an event or by scheduling them to run at a specific time. Defined by a YAML file in the `.github/workflows` folder.
- **Job** - a set of steps that run inside the same virtual machine runner, or inside a container. By default, they are executed in parallel. Each step is either a shell script that will be executed, or an _action_ that will be run. Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another.
- **Events** - triggers an execution of a Workflow. It could be an internal GitHub event (push, release, fork, new issues with specific label, or a pull request), a scheduled event (triggered at a specific time), or an external event (triggered by a webhook call to the GitHub API).
- **Actions** - (usually) created by public community  snippets for solving popular tasks in Workflows.
- **Runners** - is a virtual machine that runs a job. The runner is responsible for looking for the available jobs, then executes each job at a time. After the job is finished running, the runner reports the progress and logs of the job to GitHub.

## Logic

### Artifacts
Artifacts are used for sharing data between jobs, it also saves data once the workflow is finished, also are generally used to save logs and reports of your workflow.

```yaml
# upload artifact
- name: Upload deployable package
  uses: actions/upload-artifact@v2
  with:
    name: production-files
    path: path/to/artifact

# dowload artifact
- name: Download artifact
  uses: actions/download-artifact@v2
  with:
    name: production-files
    path: path/to/artifact 
```

### Cache

GitHub Workflow runs often reuse the same downloaded dependencies from one run to another. For example, package and dependency management tools such as npm and pip keep a local cache of downloaded dependencies.
To cache dependencies for a job, you'll need to use GitHub's cache action. This action retrieves a cache identified by a unique key.

actions themselves have 3 parameters
- `path` **(**required): The file path on the runner to cache or restore. The path can be an absolute path or relative to the working directory.
- `key` **(**required): The key created when saving a cache and the key used to search for a cache. It tells GitHub Actions how to uniquely identify each version of your cache.
- `restore-keys` **(**optional): An ordered list of alternative keys to find the cache if no cache hit occurred for `key`.

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

### Actions

- `uses` : This value takes the format of `action-name/version` or `github-repo-owner/repo-name`.
- `with` : The value is an input if the action requires one.

ways to reference a public action from the marketplace.
1. Referencing a branch
2. Referencing a version
3. Referencing a commit

```yaml
steps:
 - name: step-name
   uses: user/repo-name@branch/version/commit-name
   with: #inputs
     fetch-depth: 0
```