# Yggdrasil: API & External Interfaces

## Content Interfaces

*   **Markdown Files with Front-Matter:** The primary input interface for content. Each Markdown file includes a YAML front-matter section with structured metadata such as `title`, `owners`, `last_updated`, `tags`, and `version`. This metadata is crucial for programmatic processing and search.

## User Interfaces

*   **MkDocs Site:** Humans can browse the knowledge base through the generated MkDocs site, typically hosted at an internal URL like `https://kb.internal`. This provides a user-friendly, navigable web interface.
*   **GitHub Repository:** Users can directly browse the Markdown files in the GitHub repository, offering a raw view of the content and its version history.
*   **Knowledge Base (KB) Query:** AI agents and advanced users can query the vector KB with filters (e.g., `{"domain": "policy", "tags": ["security"]}`). This enables precise and semantic search capabilities.

## Automation Interfaces

*   **GitHub Actions Workflows:**
    *   `lint.yml`: Triggers on Pull Requests to perform `markdownlint`, `yamllint`, and link checking, ensuring content quality and consistency.
    *   `site.yml`: Triggers on merge to `main` to build the MkDocs site, push to the `docs/` branch (for static site hosting), and call the KB ingest service.
    *   `roster.yml`: Runs nightly to rebuild `members/index.md` (auto-generated roster) and flag missing bios, ensuring the team directory is always current.
*   **KB Ingest Service:** Receives a webhook call from the `site.yml` workflow to ingest updated content into the vector KB. This service is responsible for parsing Markdown, extracting metadata, and creating vector embeddings.

## Cross-Referencing Interfaces

*   **Relative Paths:** Cross-links within the documentation use relative paths, ensuring they work seamlessly in both raw GitHub and the built MkDocs site, promoting content portability.
*   **Links to Runebook:** Project pages in Yggdrasil link out to Runebook for deep technical details related to code. This establishes a clear separation of concerns between organizational knowledge and code-specific documentation.

<!-- interfaces.md last updated from commit: f8eff3399ad574751ee04eebfd84fa32bdd25111 -->