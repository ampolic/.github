# ampolic/.github

Org-level shared GitHub Actions workflows. Lives in a **public** repo because
GitHub only lets public repos call reusable workflows hosted publicly.

- `.github/workflows/site-ci.yml` — CI for every Ampolic site repo
  (install with GitHub Packages auth → `astro check` → build). Sites call it:

  ```yaml
  jobs:
    build:
      uses: ampolic/.github/.github/workflows/site-ci.yml@main
      with: { node-version: '22' }
      secrets: { packages-token: ${{ secrets.PACKAGES_TOKEN }} }
  ```

Branch model: `dev` (default, working) → `main` via PR. Keep this repo free of
any company-internal knowledge — that lives in the private `ampolic-core`.
