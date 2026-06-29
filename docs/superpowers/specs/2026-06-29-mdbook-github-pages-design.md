# mdBook GitHub Pages Design

## Goal

Create a public GitHub repository at `Chivier/ai-tutorial-in-2026` that builds this tutorial with mdBook in CI and publishes the generated HTML with GitHub Pages.

## Scope

- Initialize the current folder as a git repository on `main`.
- Keep the existing `toc_plan.md` as the source planning artifact.
- Add a buildable mdBook project under `src/`.
- Add GitHub Actions CI for `mdbook build`.
- Deploy the `book/` artifact to GitHub Pages from `main`.
- Invite `VanillaAwA` as a collaborator with write access.

## Architecture

The repository stores only source markdown and configuration. CI installs a pinned mdBook version, builds the static site, uploads the generated `book/` directory as a Pages artifact, and deploys it through the GitHub Pages Actions runtime.

## Validation

- `mdbook build` must pass locally.
- The workflow must be present under `.github/workflows/pages.yml`.
- The remote repository must be public and pushed.
- GitHub Pages must use workflow deployment.
- `VanillaAwA` must have a repository invitation or collaborator entry.

