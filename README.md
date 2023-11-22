## Test 1: All defaut values

1. Open GitHub Actions and run the "Workflow One" workflow.
2. Open the "Workflow One" workflow and click on the "Test job 1" job.
3. Expand the "Set output vars" step and check the output.

**Expected output:**

```yaml
env:
  TF_VAR_custom_one: one
  TF_VAR_custom_two: two
  TF_VAR_custom_three: three
```


## Test 2: Custom input value

1. Open GitHub Actions and run the "Workflow One" workflow.
2. In the Run dialog box, enter the following value for the `Custom input variable` input: `custom_one`
3. Click on the "Run workflow" button.

**Expected output:**

1. Open the "Workflow One" workflow and click on the "Test job 1" job.
2. Expand the "Set output vars" step and check the output.

```yaml
env:
  **TF_VAR_custom_one: custom_one**
  TF_VAR_custom_two: two
  TF_VAR_custom_three: three
```

## Test 3: Custom GitHub Actions input value

1. Go to the repository settings
2. Go to the "Secrets and variables" tab => "Variables" section
3. Create a new variable `TF_VAR_CUSTOM_TWO` with the value `custom_two`
4. Open GitHub Actions and run the "Workflow One" workflow.
5. Click on the "Run workflow" button.


**Expected output:**

1. Open the "Workflow One" workflow and click on the "Test job 1" job.
2. Expand the "Set output vars" step and check the output.

```yaml
env:
  TF_VAR_custom_one: one
  **TF_VAR_custom_two: custom_two**
  TF_VAR_custom_three: three
```

## Test 4: Read from file

1. Create `./terraform/demo.env`` file with the following content:
   TF_VAR_custom_three=custom_three
2. Commit file into the repository
3. Open GitHub Actions and run the "Workflow One" workflow.
4. Click on the "Run workflow" button.

**Expected output:**

1. Open the "Workflow One" workflow and click on the "Test job 1" job.
2. Expand the "Set output vars" step and check the output.

```yaml
  env:
    TF_VAR_custom_one: one
    TF_VAR_custom_two: two
    **TF_VAR_custom_three: custom_three**
```

## Test 5: Reusable workflows

1. Open GitHub Actions and run the "Workflow Two" workflow.
2. Open the "Workflow Two" workflow 

**Expected output:**

1. Click on the "Test job 1" job.
2. Expand the "Set output vars" step and check the output.

```yaml
 env:
    **TF_VAR_custom_one: custom_workflow_two**
    TF_VAR_custom_two: two
    TF_VAR_custom_three: three
```

1. Click on the "Test job 2" job.
2. Expand the "Print output" step and check the output.

```
  The output is custom_workflow_two
```