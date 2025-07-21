# Yggdrasil: Operational Workflows

## Contribution Workflow

1.  **Fork and Branch:** Fork the repository and create a new topic branch for your changes.
2.  **Add or Edit Content:** Add or edit Markdown files within the appropriate directories (e.g., `01-projects/`, `02-team/`, `03-policies/`).
3.  **Update `last_updated`:** Ensure the `last_updated` field in the front-matter of modified files is updated to the current date.
4.  **Linting:** Run `make lint` (or equivalent linting commands) to ensure compliance with style guidelines and catch common errors.
5.  **Open Pull Request (PR):** Open a PR for your changes, providing a clear description of the contribution.
6.  **Lead Review:** At least one lead must review and approve the PR before merging.
7.  **Policy Changes:** For policy changes, add the `policy-change` label to the PR, which triggers a Slack approval workflow for additional oversight.

## CI/CD Workflows

Yggdrasil leverages GitHub Actions for automated CI/CD processes:

*   **`lint.yml`:**
    *   **Trigger:** Pull Request.
    *   **Steps:** Runs `markdownlint`, `yamllint`, and a link checker to ensure content quality, consistency, and prevent broken links.
*   **`site.yml`:**
    *   **Trigger:** Merge to `main` branch.
    *   **Steps:** Builds the MkDocs site, pushes the generated site to the `docs/` branch (for GitHub Pages deployment), and calls the KB ingest service to update the vector knowledge base.
*   **`roster.yml`:**
    *   **Trigger:** Nightly cron job.
    *   **Steps:** Rebuilds `members/index.md` (auto-generated roster) and flags any missing bios, ensuring the team directory is always current.

## Onboarding Workflow (New Hire)

1.  **Read Core Values:** Read `02-team/mission-vision-core-values.md` to understand the organizational foundation.
2.  **Skim Coding Conventions:** Skim `03-policies/coding-conventions.md` for basic development guidelines.
3.  **Locate Project:** Locate your assigned project in `01-projects/`.
4.  **Explore Runebook**: Follow the link to Runebook and open `overview.md` for technical details of the project.
5.  **Add Your Bio:** Add your biography under `02-team/members/` to become part of the team roster.

<!-- workflows.md last updated from commit: f8eff3399ad574751ee04eebfd84fa32bdd25111 -->