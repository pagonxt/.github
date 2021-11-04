# MS Team Github Actions integration

### Usage

1. `MS_TEAMS_WEBHOOK_URI` is a PagoNxt organization secrets. Contain the webhook uri to send New Releases PagoNxt Channel. It is the [webhook URI](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook) of the dedicated Microsoft Teams channel for notification.

2. Add a new `New Workflow` from Actions Tabs on your repository´s selecting Releases Notifier of Workflows created by PagoNxt list. Or Create new workflow file named 'release-notify.yml' with the code set out below:

```yaml
## Name file: release-notify.yml
name: Releases Notifier
on:
  release:
    types: [ released ]
jobs:
  Post_New_Release_in_Teams:
    runs-on: [ self-hosted, ubuntu-latest ]
    steps:
      - name: Get PagoNxt token for dependencies
        id: dependencies
        uses: getsentry/action-github-app-token@v1
        with:
          app_id: ${{ secrets.DEPENDENCIES_APP_ID }}
          private_key: ${{ secrets.DEPENDENCIES_PRIVATE_KEY }}
      - uses: actions/checkout@v2
        with:
          repository: pagonxt/gha-teams-notify
          token: ${{ steps.dependencies.outputs.token }}
          ref: main
          path: actions/gha-teams-notify
      - name: Send Notification to New Releases Channel
        uses: ./actions/gha-teams-notify
        if: always()
        with:
          github-token: ${{ github.token }}
          webhook-uri:  ${{ secrets.MS_TEAMS_RELEASES_WEBHOOK_URI }}
```

### Known Issues

- Always set this step with `if: always()` when there are steps between `actions/checkout@v2` and this step.


### References
- [Click on GH Action Based](https://github.com/pagonxt/gha-teams-notify)
