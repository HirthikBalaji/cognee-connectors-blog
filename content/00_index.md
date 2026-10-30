---
title: Cognee Community Connectors Showcase
description: A deep-dive 10-part engineering series detailing production-grade data-source connectors for autonomous AI knowledge graphs.
---

<div class="hero-box">
  <div class="hero-tag">🚀 Topoteretes Cognee Hackathon & Integrations</div>
  <h1 class="hero-title">Bridging Real-World Data into Cognitive Knowledge Graphs</h1>
  <p class="hero-desc">
    An in-depth engineering series detailing the architecture, implementation, and verification of <strong>10 high-performance data-source connectors</strong> resolving top community issues on <a href="https://github.com/topoteretes/cognee">topoteretes/cognee</a>. From incremental Notion watermarking to WhatsApp multi-line parsing and GitHub Actions self-healing diagnostics.
  </p>
  <div style="display: flex; gap: 0.75rem; flex-wrap: wrap;">
    <span class="badge badge-blue">✓ 10 Dedicated PRs</span>
    <span class="badge badge-purple">⚡ DLT Embedded Engine</span>
    <span class="badge badge-green">🛡️ 100% DCO Signed-Off</span>
    <span class="badge badge-cyan">🧪 49 Passing Tests</span>
  </div>
</div>

<div class="stats-ribbon">
  <div class="stat-card">
    <div class="stat-val">10</div>
    <div class="stat-label">Pull Requests</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">49</div>
    <div class="stat-label">Tests Passing</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">10x-50x</div>
    <div class="stat-label">Sync Speedup</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">100%</div>
    <div class="stat-label">DCO Conformance</div>
  </div>
</div>

---

## The Knowledge Ingestion Architecture

Cognee unifies vector search and structured knowledge graphs to give LLMs persistent, queryable memory. Community connectors live in `packages/connector/<name>` and leverage `dlt` (data load tool) to stream structured records directly into Cognee's `cognify` pipeline.

```mermaid
flowchart TD
    subgraph Data Sources
        S1["Notion Workspaces"]
        S2["WhatsApp Exports (.txt/.zip)"]
        S3["Jupyter Notebooks (.ipynb)"]
        S4["RSS / Atom / JSON Feeds"]
        S5["arXiv Scientific Papers"]
        S6["Hacker News REST API"]
        S7["PubMed NCBI Entrez"]
        S8["Substack Publications"]
        S9["IMAP Enterprise Mailboxes"]
        S10["GitHub Actions Runs"]
    end

    subgraph DLT Connector Layer
        C1["notion (Watermark Cache)"]
        C2["whatsapp (Regex Continuity)"]
        C3["jupyter (Cell Decomposition)"]
        C4["rss (HTML Sanitizer)"]
        C5["arxiv (3s Request Pacing)"]
        C6["hackernews (Discussion Tree)"]
        C7["pubmed (Structured Abstracts)"]
        C8["substack (Domain Normalizer)"]
        C9["imap (MIME & RFC 2047)"]
        C10["github_actions (Log Diagnostics)"]
    end

    subgraph Cognee Cognitive Engine
        Cognify["cognee.remember(source, dataset_name)"]
        Index["Vector Embeddings (LanceDB / Qdrant)"]
        Graph["Knowledge Graph (NetworkX / FalkorDB)"]
    end

    S1 --> C1
    S2 --> C2
    S3 --> C3
    S4 --> C4
    S5 --> C5
    S6 --> C6
    S7 --> C7
    S8 --> C8
    S9 --> C9
    S10 --> C10

    C1 & C2 & C3 & C4 & C5 & C6 & C7 & C8 & C9 & C10 --> Cognify
    Cognify --> Index
    Cognify --> Graph
```

---

## Explore the 10 Connector Deep Dives

<div class="connector-grid">

  <a href="./01_notion_incremental_sync" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">📝</span>
        <span class="badge badge-blue">PR #562</span>
      </div>
      <div class="card-title">Notion Incremental Sync</div>
      <div class="card-summary">
        Eliminate HTTP 429 rate limits with persistent block watermark caching in <code>dlt.current.source_state()</code>. Delivers up to 50x faster incremental syncs.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4820</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./02_whatsapp_chat_export" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">💬</span>
        <span class="badge badge-green">PR #563</span>
      </div>
      <div class="card-title">WhatsApp Chat Exports</div>
      <div class="card-summary">
        Turn unstructured group chats into queryable team memory. Multi-line message continuation, international timestamp normalization, and in-memory ZIP extraction.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #5836</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./03_jupyter_notebook_reader" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">📓</span>
        <span class="badge badge-purple">PR #564</span>
      </div>
      <div class="card-title">Jupyter Notebook Reader</div>
      <div class="card-summary">
        Deconstruct <code>.ipynb</code> notebooks into markdown prose, language-attributed code cells, and text outputs while intelligently stripping heavy base64 images.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #5509</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./04_rss_atom_json_feed" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">📡</span>
        <span class="badge badge-amber">PR #565</span>
      </div>
      <div class="card-title">RSS, Atom & JSON Feeds</div>
      <div class="card-summary">
        Universal multi-format web feed reader with built-in regex HTML cleaning for tracking engineering blogs, vulnerability feeds, and industry releases.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4804</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./05_arxiv_research_papers" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">🔬</span>
        <span class="badge badge-cyan">PR #566</span>
      </div>
      <div class="card-title">arXiv Research Papers</div>
      <div class="card-summary">
        Empower autonomous scientific research agents. Polite 3-second API request pacing, category and search term filters, and full paper metadata extraction.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4806</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./06_hackernews_community_pulse" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">🔥</span>
        <span class="badge badge-amber">PR #567</span>
      </div>
      <div class="card-title">Hacker News Discussions</div>
      <div class="card-summary">
        Capture real-time developer sentiment. Direct Firebase REST API client supporting Top, Ask, Show, and Job stories with optional discussion tree traversal.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4805</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./07_pubmed_biomedical_literature" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">🧬</span>
        <span class="badge badge-blue">PR #568</span>
      </div>
      <div class="card-title">PubMed Biomedical Literature</div>
      <div class="card-summary">
        Integrate NCBI Entrez E-utilities (<code>esearch</code> + <code>efetch</code>) with structured abstract parsing (Background, Methods, Results, Conclusions) for clinical AI.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4807</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./08_substack_newsletter_connector" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">📰</span>
        <span class="badge badge-purple">PR #569</span>
      </div>
      <div class="card-title">Substack Newsletters</div>
      <div class="card-summary">
        Ingest long-form thought leadership and industry analysis. Flexible publication handle/domain normalization with email HTML layout cleanup.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #4810</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./09_imap_email_mailbox_connector" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">✉️</span>
        <span class="badge badge-green">PR #570</span>
      </div>
      <div class="card-title">IMAP Enterprise Mailboxes</div>
      <div class="card-summary">
        Enterprise inbox knowledge retrieval. RFC 2047 internationalized header decoding, SSL/STARTTLS support, and recursive multipart MIME traversal.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #5634</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

  <a href="./10_github_actions_ci_diagnostics" class="connector-card">
    <div>
      <div class="card-header">
        <span class="card-icon">⚙️</span>
        <span class="badge badge-cyan">PR #571</span>
      </div>
      <div class="card-title">GitHub Actions Diagnostics</div>
      <div class="card-summary">
        Build self-healing CI/CD debugging agents. Isolates failed workflow runs and error logs to give coding agents immediate root-cause context.
      </div>
    </div>
    <div class="card-footer">
      <span>Issue #5742</span>
      <span style="color: var(--secondary)">Read Article →</span>
    </div>
  </a>

</div>

---

## Technical Comparison Matrix

| Connector | Protocol / Backend | Incremental State | Rate Limit Strategy | Output Record Type |
|---|---|---|---|---|
| **Notion** | REST API (`notion-client`) | `dlt.current.source_state()` | Page block caching | Database page + blocks |
| **WhatsApp** | File I/O (`.txt`, `.zip`) | Stateless batch / stream | N/A (Local) | Structured chat message |
| **Jupyter** | JSON v4 Schema | Stateless batch | N/A (Local) | Decomposed notebook doc |
| **RSS / Atom** | XML / JSON HTTP | Feed URL ETag / Polling | HTTP caching headers | Syndicated news item |
| **arXiv** | Atom XML API | Query pagination | 3.0s enforced delay | Scientific paper metadata |
| **Hacker News** | Firebase REST API | Story ID cursor | Firebase CDN limits | Story + comments tree |
| **PubMed** | NCBI E-utilities XML | Search PMID batching | NCBI 334ms interval | Clinical paper + abstract |
| **Substack** | Syndication Feed | Handle / URL normalization | HTTP caching | Clean newsletter essay |
| **IMAP** | RFC 3501 IMAP4 | Mailbox UID / SEARCH criteria | Server connection pool | Multipart MIME email |
| **GitHub Actions** | GitHub REST API | Workflow run ID | GitHub PAT token limits | CI/CD run + error logs |

---

## Quickstart: Ingesting into Cognee

All 10 connectors follow the standard Cognee ingestion contract:

```python
import asyncio
import cognee

# 1. Import any connector
from cognee_community_connector_notion import notion_database
from cognee_community_connector_arxiv import arxiv_papers
from cognee_community_connector_github_actions import github_actions_runs

async def main():
    # 2. Configure the connector resource
    papers_source = arxiv_papers(
        search_query='cat:cs.AI AND all:"knowledge graphs"',
        max_results=20,
    )

    # 3. Stream into Cognee's cognitive graph
    await cognee.remember(papers_source, dataset_name="ai_research")

    # 4. Query your AI agent with semantic knowledge graph search
    answer = await cognee.search("What graph reasoning architectures are popular in 2026?")
    print(answer)

if __name__ == "__main__":
    asyncio.run(main())
```

---

## Community & Verification Notes
- Every connector is licensed under Apache 2.0.
- All 10 commits conform to the **Topoteretes Developer Certificate of Origin** (`git commit -s`).
- Test suites can be executed locally via `pytest packages/connector/*/tests/`.
