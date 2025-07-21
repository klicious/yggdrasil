# Yggdrasil: System Architecture

## High-Level Diagram

```mermaid
flowchart TD
    A[Markdown Files (Content)] --> B(GitHub Repository)
    B --> C[GitHub Actions (CI/CD)]
    C --> D[MkDocs Site Generation]
    D --> E[Internal MkDocs Site]
    C --> F[Vector Knowledge Base Ingest]
    F --> G[Vector Knowledge Base (KB)]
    G --> H[Human Users & AI Agents]
```

## Component Breakdown

*   **Markdown Files (Content)**: The core content of Yggdrasil, organized into logical directories (e.g., `01-projects/`, `02-team/`, `03-policies/`). Each file includes YAML front-matter for structured metadata.
*   **GitHub Repository**: Serves as the version control system for all Markdown content, enabling collaboration, history tracking, and pull request workflows.
*   **GitHub Actions (CI/CD)**: Automated workflows that trigger on various events (e.g., pull requests, merges to `main`). Key workflows include:
    *   `lint.yml`: For linting Markdown and YAML files, and checking links.
    *   `site.yml`: For building the MkDocs site and ingesting content into the Vector Knowledge Base.
    *   `roster.yml`: For rebuilding the member roster.
*   **MkDocs Site Generation**: Uses MkDocs to transform Markdown files into a navigable static website.
*   **Internal MkDocs Site**: The human-readable web interface for browsing Yggdrasil content.
*   **Vector Knowledge Base Ingest**: A process (triggered by `site.yml`) that extracts content from the Markdown files and indexes it into a Vector Knowledge Base.
*   **Vector Knowledge Base (KB)**: A searchable database that stores content embeddings, enabling advanced semantic search and retrieval for both human users and AI agents.

## Data Flow

1.  **Content Creation**: Authors create or update Markdown files with front-matter.
2.  **Version Control**: Changes are committed to the GitHub repository.
3.  **CI/CD Trigger**: GitHub Actions workflows are triggered by commits or pull requests.
4.  **Site Generation**: The `site.yml` workflow builds the MkDocs site from the Markdown content.
5.  **KB Ingestion**: Concurrently, the `site.yml` workflow triggers the KB ingest process, which extracts and indexes content into the Vector Knowledge Base.
6.  **Access**: Human users access the MkDocs site or query the KB directly. AI agents primarily query the KB for information.

## Deployment Model

Yggdrasil is deployed as a static website and an indexed knowledge base:

*   **MkDocs Site**: Deployed as a static site (e.g., GitHub Pages) for internal access.
*   **Vector Knowledge Base**: The KB is typically hosted on a dedicated service or infrastructure that supports vector embeddings and search.

<!-- architecture.md last updated from commit: f8eff3399ad574751ee04eebfd84fa32bdd25111 -->