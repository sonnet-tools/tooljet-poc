# tooljet-poc

Replica of ToolJet/ToolJet's `render-preview-deploy.yml` workflow.

Demonstrates issue_comment body injection vulnerability:
- Workflow triggers on `issue_comment` with `contains(body, '/deploy-ee')`
- No collaborator/association gate — any external user can trigger
- `${{ github.event.comment.body }}` injected into bash `[[ ]]` comparison
- Attacker breaks out of string comparison to execute arbitrary commands
- Secrets: RENDER_API_KEY, CUSTOM_GITHUB_TOKEN, SMTP creds, MARKETPLACE_BUCKET

Used for authorized security research only.
