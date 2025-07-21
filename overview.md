
# Yggdrasil Project Overview

## Project Purpose

Yggdrasil serves as the organization's **living handbook** and centralized knowledge repository - the "world-tree" of operational wisdom that contains everything beyond source code. It is the single source of truth for mission statements, member biographies, organizational policies, standard operating procedures (SOPs), and high-level project dashboards.

As the organizational memory system, Yggdrasil complements the technical depth found in Runebook by providing the human-centered knowledge needed for effective team coordination and institutional knowledge preservation.

## Core Technologies

* **Markdown**: Primary format for all documentation files with enforced front-matter contracts
* **MkDocs + Material**: Static site generator for the internal documentation website (https://kb.internal)
* **GitHub Actions**: Automated workflows for linting, site deployment, and vector knowledge base ingestion
* **Vector Knowledge Base**: Integration for AI-powered search and retrieval by both humans and agents
* **YAML Front-Matter**: Structured metadata enforcement for content governance

## Key Capabilities

* **Mission Management**: Central repository for vision, mission, and core values
* **People Management**: Member roster, role definitions, and biographical information
* **Policy Management**: Coding conventions, security policies, and governance frameworks
* **Process Management**: SOPs for product planning, execution, and cultural practices
* **Project Dashboards**: Executive summaries linking to detailed technical documentation in Runebook
* **Template Management**: Standardized templates for ADRs, OKRs, and other organizational artifacts

## Developer Setup

### Contributing to Yggdrasil

1. **Fork and Branch**: Fork the repository and create a topic branch for your changes
2. **Content Creation**: Add or edit Markdown files following the established directory structure
3. **Metadata Requirements**: Ensure all files include required front-matter (owners, last_updated, valid ISO date)
4. **Quality Assurance**: Run `make lint` to validate markdown, YAML, and link integrity
5. **Review Process**: Submit PR requiring at least one lead review; policy changes require additional approval workflow

### Repository Integration

* **Cross-linking**: Use relative paths for seamless navigation between GitHub and built site
* **Runebook Integration**: Project pages link to detailed technical documentation
* **Knowledge Base Sync**: Content automatically ingested into searchable vector store with "yggdrasil-*" collection prefixes
