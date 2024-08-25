# Generate GitHub Apps Token

## example

```yml
    steps:
      - uses: hakadoriya/github-actions-github-apps-token@main
        id: github-apps-token
        with:
          app-id: ${{ secrets.APP_ID }}
          private-key: ${{ secrets.PRIVATE_KEY }}
      - name: "Run steps that require a GitHub token"
        env:
          GITHUB_TOKEN: ${{ steps.github-apps-token.outputs.token }}
        run: |
          gh pr comment --body "Test comment"
```
