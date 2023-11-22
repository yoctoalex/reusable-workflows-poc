TF_VAR_custom_one: "one"
TF_VAR_custom_two: "two"
TF_VAR_custom_three: "three"

TF_VAR_CUSTOM_TWO

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
2. In the Run dialog box, enter the following value for the `Custom input variable` input: `custom_input "custom_one"`
3. Clich on the "Run workflow" button.
4. Open the "Workflow One" workflow and click on the "Test job 1" job.
5. Expand the "Set output vars" step and check the output.

**Expected output:**

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
5. Clich on the "Run workflow" button.
6. Open the "Workflow One" workflow and click on the "Test job 1" job.
7. Expand the "Set output vars" step and check the output.

**Expected output:**

```yaml
env:
  TF_VAR_custom_one: one
  **TF_VAR_custom_two: custom_two**
  TF_VAR_custom_three: three
```
