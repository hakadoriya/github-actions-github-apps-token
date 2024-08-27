# Generate GitHub Apps Token for GitHub Actions

## Register new GitHub App

- If creating a personal GitHub App,
  - <https://github.com/settings/apps/new>
- If creating an organization GitHub App,
  - <https://github.com/organizations/ORGANIZATION/settings/apps/new>
- If not needed, remove the `Active` check from `Webhook`.

## example

```yml
    steps:
      - uses: hakadoriya/github-actions-github-apps-token@main
        id: github-apps-token
        with:
          client-id: ${{ secrets.GH_APPS_CLIENT_ID }}
          private-key: ${{ secrets.GH_APPS_PRIVATE_KEY }}
          jwt-expiry-seconds: 300
      - name: "Run steps that require a GitHub token"
        env:
          GITHUB_TOKEN: ${{ steps.github-apps-token.outputs.token }}
        run: |
          gh pr comment --body "Test comment"
```
