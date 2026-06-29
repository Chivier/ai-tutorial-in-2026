# mdBook GitHub Pages Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and publish the tutorial as an mdBook site from a new public GitHub repository.

**Architecture:** The repo contains markdown source in `src/`, mdBook settings in `book.toml`, and one GitHub Actions workflow that builds on PRs and deploys Pages on `main`. The generated `book/` output is ignored locally and uploaded only as a CI artifact.

**Tech Stack:** mdBook 0.4.52, GitHub Actions, GitHub Pages, GitHub CLI.

---

### Task 1: Repository Scaffold

**Files:**
- Create: `.gitignore`
- Create: `README.md`
- Create: `book.toml`
- Create: `src/SUMMARY.md`
- Create: `src/part-*/*.md`

- [ ] Add mdBook configuration and source markdown.
- [ ] Run `mdbook build` and expect exit code `0`.

### Task 2: CI and Pages

**Files:**
- Create: `.github/workflows/pages.yml`

- [ ] Add a workflow that installs mdBook 0.4.52.
- [ ] Run `mdbook build` locally and expect exit code `0`.
- [ ] Push `main` to GitHub.
- [ ] Enable GitHub Pages with workflow deployment.

### Task 3: GitHub Repository

**Files:**
- No additional source files.

- [ ] Create public repository `Chivier/ai-tutorial-in-2026`.
- [ ] Push the local `main` branch.
- [ ] Invite `VanillaAwA` with write access.
- [ ] Check repository visibility and collaborator invitation status with `gh api`.

