
# Maintenance

This document provides instructions for the ongoing maintenance of the `yggdrasil` project.

## Schema Evolution

*   When schema evolution occurs, bump `schema_version` in `00-meta/glossary.md`.

## Archiving

*   Move obsolete SOPs to `04-processes/_archive/` (these are excluded from the site).

## Analytics

*   The site shows "most viewed" and "stale >6 months" pages for pruning, which can be used to identify content that needs updating or archiving.

## Contribution Guidelines

*   **Fork and Branch:** Fork the repository and create a new topic branch.
*   **Add or Edit Markdown:** Add or edit Markdown files.
*   **Update `last_updated`:** Update the `last_updated` field in the front-matter.
*   **Linting:** Run `make lint` (assuming a Makefile exists with linting commands).
*   **Open PR:** Open a Pull Request; at least one lead review is required.
*   **Policy Changes:** For policy changes, add the `policy-change` label to the PR, which triggers a Slack approval workflow.
