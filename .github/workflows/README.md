# GitHub Workflows Documentation

This directory contains GitHub Actions workflows for automating CI/CD processes.

## Workflows

### Dynamic Build and Push Custom Images

**File:** `build-and-push-images.yaml`

**Purpose:** Automatically builds and pushes custom Docker images to a container registry when changes are pushed to the repository.

**Triggers:**
- **Push events:** Triggered when code is pushed to the `main` branch
- **Pull requests:** Triggered when pull requests target the `main` branch
- **Path filtering:** Ignores changes made only to `.github/**` directory

**Permissions:**
- `contents: read` - Allows reading repository contents
- `packages: write` - Allows pushing images to GitHub Container Registry (ghcr.io)

**Jobs:**

#### dynamic-build-and-push
- **Name:** Dynamic Build and Push Docker Images Caller
- **Type:** Reusable workflow call
- **Source:** Uses the `dynamic-build-and-push.yaml` workflow from the `srekit/github-workflows` repository (main branch)
- **Description:** Delegates the actual build and push logic to a centralized, reusable workflow

**How it works:**
1. When code is pushed to `main` or a PR is opened targeting `main`
2. If the changes are outside the `.github/` directory
3. The workflow calls the reusable workflow from `srekit/github-workflows`
4. The reusable workflow handles Docker image building and pushing to the container registry

**Notes:**
- The workflow uses a reusable pattern to maintain consistency across repositories
- Changes to workflow files themselves (`.github/**`) do not trigger builds to avoid unnecessary runs
