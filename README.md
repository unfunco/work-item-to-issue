# Create GitHub Issues from Azure DevOps Work Items

A GitHub Action that syncs Azure DevOps work items to GitHub issues, with
optional assignment to Copilot for automated coding.

```yaml
name: Sync Azure DevOps work items

on:
  schedule:
    - cron: '*/15 * * * *'
  workflow_dispatch: { }

jobs:
  sync:
    name: Sync
    permissions:
      contents: read
      id-token: write
      issues: write
    runs-on: ubuntu-slim
    steps:
      - name: Sync work items to GitHub issues
        uses: unfunco/work-item-to-issue@v0.1.0
        with:
          azure-client-id: ${{ secrets.AZURE_CLIENT_ID }}
          azure-tenant-id: ${{ secrets.AZURE_TENANT_ID }}
          azure-devops-url: ${{ vars.AZURE_DEVOPS_URL }}
          azure-devops-project: ${{ vars.AZURE_DEVOPS_PROJECT }}
          azure-devops-label: 'copilot:ready'
          assign-to-copilot: true
          github-token: ${{ secrets.COPILOT_USER_TOKEN }}
```

## Random Quote

> “Simplicity is prerequisite for reliability.” — Edsger W. Dijkstra

## License

© 2026 [Daniel Morris]\
Made available under the terms of the [MIT License].

[daniel morris]: https://unfun.co
[mit license]: LICENSE.md
