# checks-complete-action

Single required status check for multi-job GitHub Actions workflows.

## Usage

All the following to a workflow that you want to enforce required status checks on:

```yaml
checks-complete:
  needs: [job1, job2, job3] # List all jobs that must complete successfully
  if: always() # Ensure this job runs regardless of previous job outcomes
  uses: hotdog-werx/checks-complete-action/.github/workflows/verify.yaml@v0
  with:
    needs-jobs: '${{ toJSON(needs) }}'
```

Then, in your repository settings, set the `checks-complete / verify` job as a required status check for your branch protection rules.

## Inputs

`needs-jobs` (required): This is required to be `'${{ toJSON(needs) }}'` so that the action can parse the list of jobs that need to complete successfully.
