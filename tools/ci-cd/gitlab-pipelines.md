# 🦊 Gitlab pipelines

#### Info

A pipeline is composed of independent jobs that run scripts, grouped into stages. Stages run in sequential order, but jobs within stages run in parallel.

#### Links

doc - [https://docs.gitlab.com/ee/ci/](https://docs.gitlab.com/ee/ci/)

#### Filename

```
.gitlab-ci.yml
```

#### File Structure

```yaml
# List of stages for jobs, and their order of execution
stages:          
  - build
  - test
  - deploy
# This job runs in the build stage, which runs first.
build-job:       
  stage: build
  script:
    - echo "Compiling the code..."
    - echo "Compile complete."

# This job runs in the test stage.
unit-test-job:   
  stage: test    # It only starts when the job in the build stage completes successfully.
  script:
    - echo "Running unit tests... This will take about 60 seconds."
    - sleep 60
    - echo "Code coverage is 90%"

# This job also runs in the test stage.
lint-test-job:   
  stage: test    # It can run at the same time as unit-test-job (in parallel).
  script:
    - echo "Linting code... This will take about 10 seconds."
    - sleep 10
    - echo "No lint issues found."

# This job runs in the deploy stage.
deploy-job:      
  stage: deploy  # It only runs when *both* jobs in the test stage complete successfully.
  environment: production
  script:
    - echo "Deploying application..."
    - echo "Application successfully deployed.
```

## Jobs

### Job name limitations

You can’t use these keywords as job names:

* `image`
* `services`
* `stages`
* `types`
* `before_script`
* `after_script`
* `variables`
* `cache`
* `include`
* `true`
* `false`
* `nil`

Job names must be 255 characters or fewer.

Use unique names for your jobs. If multiple jobs have the same name, only one is added to the pipeline, and it’s difficult to predict which one is chosen.



