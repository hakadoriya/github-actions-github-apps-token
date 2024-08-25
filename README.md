# Generate GitHub Apps Token

## example

```yml
    steps:
      - uses: hakadoriya/github-actions-github-apps-token@main
        id: github-apps-token
        with:
          app-id: ${{ secrets.GH_APPS_APP_ID }}
          private-key: ${{ secrets.GH_APPS_PRIVATE_KEY }}
      - name: "Run steps that require a GitHub token"
        env:
          GITHUB_TOKEN: ${{ steps.github-apps-token.outputs.token }}
        run: |
          gh pr comment --body "Test comment"
```
