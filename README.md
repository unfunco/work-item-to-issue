# Create GitHub Issues from Azure DevOps Work Items

```yaml
name: Sync Azure DevOps work items

on:
  schedule:
  - cron: '*/15 * * * *'
  workflow_dispatch: { }

permissions:
  contents: read
  id-token: write
  issues: write

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
    - name: Sync work items to GitHub issues
      uses: unfunco/work-item-to-issue@v1
      with:
        azure-client-id: ${{ secrets.AZURE_CLIENT_ID }}
        azure-tenant-id: ${{ secrets.AZURE_TENANT_ID }}
        azure-devops-url: ${{ vars.AZURE_DEVOPS_URL }}
        azure-devops-project: ${{ vars.AZURE_DEVOPS_PROJECT }}
        azure-devops-label: ${{ vars.AZURE_DEVOPS_LABEL }}
        github-token: ${{ secrets.COPILOT_USER_TOKEN }}
```
