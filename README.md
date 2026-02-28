# helmchart-repo-template

GitHub repository template for Helm charts, pre-configured with CI/CD, semantic versioning, documentation, and Renovate Bot.

## What's included

- **CI/CD** (GitHub Actions via [AutomationDojo/reusable-cicd](https://github.com/AutomationDojo/reusable-cicd))
  - PR checks: actionlint, helm lint (chart-testing), helm-docs auto-update
  - Release: semantic-release → helm chart version bump → publish to GHCR + GitHub Pages → MkDocs deploy
- **Semantic Release** with `semantic-release-helm` — automatic versioning from Conventional Commits
- **helm-docs** — auto-generated `README.md` from `values.yaml` comments
- **Artifact Hub** metadata (`artifacthub-pkg.yml`) auto-updated on each release
- **MkDocs Material** documentation site, published to `gh-pages`
- **Renovate Bot** — dependency updates

## Usage

1. Click **"Use this template"** on GitHub to create a new repository.
2. The `Init Repository` workflow runs automatically on the first push to `main`.
3. It will:
   - Run `helm create charts/<repo-name>` to scaffold a fresh Helm chart.
   - Replace all placeholders across config files with the repo name and owner.
   - Create `artifacthub-pkg.yml` and `README.md.gotmpl` for the chart.
   - Delete itself and commit everything with `[skip ci]`.

## Required secrets

| Secret | Description |
|---|---|
| `GITHUB_APP_ID` | GitHub App ID used for automation commits |
| `GITHUB_APP_PRIVATE_KEY` | GitHub App private key |
