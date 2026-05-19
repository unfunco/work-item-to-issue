# Create GitHub Issues from Azure DevOps Work Items

```yaml
name: Create Issues

on:
  schedule:
  - cron: '*/15 * * * *'
  workflow_dispatch: { }

jobs:
  create-issues:
    runs-on: ubuntu-latest
    steps:
    - name: Create from Azure DevOps Work Items
      uses: ./.github/actions/create-issues
      with:
        azure-devops-organization: ${{ secrets.AZURE_DEVOPS_ORGANIZATION }}
        azure-devops-project: ${{ secrets.AZURE_DEVOPS_PROJECT }}
        azure-devops-pat: ${{ secrets.AZURE_DEVOPS_PAT }}
        github-repository: ${{ github.repository }}
        github-token: ${{ secrets.GITHUB_TOKEN }}
```
