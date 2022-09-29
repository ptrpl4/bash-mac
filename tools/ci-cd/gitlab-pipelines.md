# 🦊 Gitlab pipelines

### Info

A pipeline is composed of independent jobs that run scripts, grouped into stages. Stages run in sequential order, but jobs within stages run in parallel.

### .gitlab-ci.yml

structure

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
