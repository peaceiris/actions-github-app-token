# GitHub App Token Action

A fork of [tibdex/github-app-token](https://github.com/tibdex/github-app-token).

# Example Workflow

```yaml
name: "Pull Request Labeler"

on:
  pull_request_target:

jobs:
  triage:
    runs-on: ubuntu-20.04
    timeout-minutes: 1
    permissions: {}
    steps:
      - uses: peaceiris/github-app-token@v1.0.4
        id: app
        with:
          app_id: ${{ secrets.GH_APP_ID }}
          private_key: ${{ secrets.GH_APP_PRIVATE_KEY }}

      # https://github.com/actions/labeler
      - uses: actions/labeler@v4
        with:
          repo-token: "${{ steps.app.outputs.token }}"
```
