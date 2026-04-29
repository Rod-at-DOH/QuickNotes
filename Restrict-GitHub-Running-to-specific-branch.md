# This is related to the Semantic-Versioning-Workflow-with-Deployment.yml

This is to that YAML file, in the FPTimetrackCore repo. I want to restrict it to only run if a PR is created from the `feature/get-semantic-version-numbers` branch to the `main` branch. I asked GitHub Copilot, using Claude Haiku 4.5 how to modify the existing YAML file to restrict it to the restriction I have specified.

## Here is what it gave me

To make the workflow only run when a PR is **opened** (started) from the feature/get-semantic-version-numbers branch to the main branch, you need to:
1.	Change the trigger type from closed to opened
2.	Add a condition to check the source branch using **github.head_ref**
Here's what to modify in your workflow:

### Current:
```yaml
on:
    pull_request:
      types: closed
      branches: 
        - main
      paths-ignore:
        - '.github/**'
    workflow_dispatch: # manual
```
### Change to:
```yaml
on:
    pull_request:
      types: opened
      branches: 
        - main
      paths-ignore:
        - '.github/**'
    workflow_dispatch: # manual

jobs:
    Find-Version-Numbers:
        if: github.head_ref == 'feature/get-semantic-version-numbers'
        runs-on: self-hosted
        env:
```

The key changes:
•	**types: closed → types: opened** (triggers when PR is created)
•	Add **if: github.head_ref == 'feature/get-semantic-version-numbers'** to the job (filters by source branch)

This ensures the workflow only runs when:

•	A pull request is **opened** (not closed)
•	The PR is targeting the **main** branch (base branch)
•	The PR is coming from the **feature/get-semantic-version-numbers** branch (head branch)
