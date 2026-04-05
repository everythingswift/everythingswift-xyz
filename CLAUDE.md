# CLAUDE.md – everythingswift-xyz

## Purpose
Central static site hosting legal pages (privacy policy, terms of use) for all EverythingSwift apps, served at everythingswift.xyz via Cloudflare Pages.

## Structure
Each app gets its own subfolder:
```
/<appname>/privacy-policy.html
/<appname>/terms-of-use.html
```

## Rules

### Secrets
- Never hardcode API tokens, account IDs, or credentials anywhere in this repo.
- All secrets (Cloudflare API token, account ID) must live in GitHub Secrets only.
- Reference them exclusively via `${{ secrets.SECRET_NAME }}` in workflow files.

### Deployment
- Deployments are handled automatically via GitHub Actions on push to `main`.
- Do not add a build step — this is a plain HTML site with no build process.
- The Cloudflare Pages project name is `everythingswift-xyz`.

### Adding a new app
- Create a new subfolder: `/<appname>/`
- Add `privacy-policy.html` and `terms-of-use.html` using the existing files as templates.
- Add a link to the new app in `index.html`.
