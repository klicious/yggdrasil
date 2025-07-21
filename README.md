# **🌳 Yggdrasil — Team-Wide Living Knowledge Base**

*Mission, policies, people, and processes—everything beyond source code.*

---

## **0. TL;DR**

Yggdrasil is the organisation’s **world-tree** of operational wisdom.

It stores mission & vision, member bios, policies, SOPs, and high-level project dashboards.

Docs are linted, rendered as an internal MkDocs site, and indexed into the vector KB so humans and agents can search “how we work” in seconds.

---

## **1. Repository Scope**

| **Domain** | **Examples** | **Deep-link** |
| --- | --- | --- |
| **Strategy** | Mission, Vision, Core Values | 02-team/mission-vision-core-values.md |
| **People** | Member cards, roles & responsibilities | 02-team/members/*.md |
| **Governance** | Coding conventions, CI/CD policy | 03-policies/*.md |
| **Processes** | PR FAQ SOP, Backward-planning | 04-processes/** |
| **Templates** | ADR stubs, OKR sheets | 05-templates/*.md |
| **Projects** | One-page exec summaries | 01-projects/*.md |

---

## **2. Directory Layout**

```
yggdrasil/
├── README.md
├── 00-meta/
│   ├── glossary.md
│   └── changelog.md
├── 01-projects/
│   ├── projA.md          ← links to Runebook architecture
│   └── projB.md
├── 02-team/
│   ├── mission-vision-core-values.md
│   ├── roles-responsibilities.md
│   └── members/
│       ├── index.md      ← auto-generated roster
│       └── kwon-tae-yeon.md
├── 03-policies/
│   ├── ci-cd.md
│   ├── coding-conventions.md
│   └── security.md
├── 04-processes/
│   ├── product-planning/
│   │   └── pr-faq-sop.md
│   ├── execution/
│   │   └── agile-work-management.md
│   └── culture/
│       ├── hiring-sop.md
│       └── evaluation-sop.md
├── 05-templates/
│   ├── adr-template.md
│   └── okr-template.md
└── .github/workflows/
    └── site.yml          ← lint + MkDocs deploy + KB ingest
```

---

## **3. Front-Matter Contract**

```
---
title: "Agile Work Management SOP"
owners: ["eng-leads@myorg.com"]
last_updated: 2025-06-25
tags: ["process", "agile"]
version: 1.0
---
```

*CI enforces presence of owners, last_updated, and valid ISO-date.*

---

## **4. Key Workflows**

| **Workflow** | **Stage** | **Steps** |
| --- | --- | --- |
| lint.yml | PR | markdownlint, yamllint, link checker |
| site.yml | Merge → main | Build MkDocs → push to docs/ branch → call KB ingest |
| roster.yml | Nightly | Rebuild members/index.md and flag missing bios |

Secrets: DOCS_SITE_TOKEN (GitHub Pages), KB_TOKEN (ingest).

---

## **5. How to Navigate**

- **Humans** – visit https://kb.internal (MkDocs) or browse in GitHub.
- **Agents** – query the KB with filter {"domain": "policy", "tags": ["security"]}.

Cross-links use **relative paths** so they work in both raw GitHub and the built site.

---

## **6. Contribution Guidelines**

1. Fork → create topic branch.
2. Add or edit Markdown.
3. Update last_updated.
4. make lint (wrapper script).
5. Open PR; at least one lead review.

*Policy changes* require ⬆️ label policy-change → triggers Slack approval workflow.

---

## **7. Relationship to Runebook**

| **Question** | **Answer** |
| --- | --- |
| Deep tech detail? | Lives in **Runebook**; Yggdrasil project pages link out. |
| Org-level decision records? | *Stay here*—Yggdrasil is the handbook. |
| KB ingestion? | Both repos point to **the same** vector store but use different collection_name prefixes (runebook-*, yggdrasil-*). |

---

## **8. Onboarding Checklist (New Hire)**

1. Read 02-team/mission-vision-core-values.md.
2. Skim 03-policies/coding-conventions.md.
3. Locate your project in 01-projects/.
4. Follow link to Runebook → open overview.md.
5. Add your bio under 02-team/members/.

---

## **9. Maintenance & Governance**

- **Schema evolution** – bump schema_version in 00-meta/glossary.md.
- **Archiving** – move obsolete SOPs to 04-processes/_archive/ (excluded from site).
- **Analytics** – site shows “most viewed” + “stale >6 months” pages for pruning.

---

## **10. FAQ**

> Q: Can I store private HR docs?
A: Redact PII; Yggdrasil is accessible to all employees and AI agents.
> 

> Q: Do I need mermaid expertise?
A: Optional—mermaid diagrams auto-render in MkDocs; fallback is plain Markdown tables.
> 

---

## **11. License & Confidentiality**

Yggdrasil content is **Internal—Strictly Confidential**.

Reuse outside the company requires written approval from Engineering Leadership.

---

*Both repositories together give every teammate—and every retrieval-augmented agent—the full 360-degree view: **Runebook** for how the code works, **Yggdrasil** for why we build and operate the way we do.*

<!-- README.md last updated from commit: f8eff3399ad574751ee04eebfd84fa32bdd25111 -->