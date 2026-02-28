# Development & Contributions

This project uses **Semantic Release** to automate versioning and package publishing.

## Conventional Commits

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. This allows us to automatically:

1. Determine the next version number (patch, minor, or major).
2. Generate a `CHANGELOG.md` file.
3. Publish GitHub releases.

### Commit Message Format

```text
<type>(<scope>): <subject>
```

### Common Types

- `feat`: A new feature (triggers a **minor** release).
- `fix`: A bug fix (triggers a **patch** release).
- `docs`: Documentation only changes.
- `refactor`: A code change that neither fixes a bug nor adds a feature.
- `chore`: Changes to the build process or auxiliary tools.

### Breaking Changes

A breaking change must be indicated by a `!` after the type/scope. This triggers a **major** release.

```text
feat!: overhaul the values structure
```

## Release Workflow

When a commit is pushed to `main`, the release pipeline will:

1. Analyse commits using Conventional Commits.
2. Update the `version` in `Chart.yaml` (via `semantic-release-helm`).
3. Generate/update the chart `CHANGELOG.md` and the root `CHANGELOG.md`.
4. Commit those changes back to the repository.
5. Create a GitHub Tag and Release.
6. Package and publish the Helm chart to `gh-pages` and GHCR.
7. Rebuild and publish the MkDocs documentation.

## Required Secrets

The repository must have the following secrets configured:

- `DEVOPS_BUDDY_APP_ID`: The ID of the GitHub App used for automation.
- `DEVOPS_BUDDY_PRIVATE_KEY`: The private key of the GitHub App.
