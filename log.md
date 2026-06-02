---
title: Work Log
description: Append-only audit trail. After each turn that creates, edits, or restructures content in the knowledge base, append one dated entry here (one per turn, not per file). Silent edits break the audit trail.
---

# Work Log

Append-only audit trail. **Append a dated entry after any turn that creates, edits, or restructures content in the knowledge base.** One entry per turn, not per file. Silent edits break the chain that makes knowledge-base changes auditable.

What to log:

- `ingest` runs (new external sources captured)
- `research` / `consolidate` runs (provisional or canonical articles produced)
- Direct `write_document` / `edit_document` / renames / deletions outside the three Karpathy-layer tools (`ingest` / `research` / `consolidate`)
- `discover` runs (project conventions extracted; folder frontmatter / templates / `.okignore` proposals applied; link-graph activations)
- Folder restructures (`ok seed`, manual reorganization)
- `.ok/config.yml` changes

**Reference docs as markdown links, not bare paths.** Every doc you touched should appear as `[path/to/doc](./path/to/doc.md)` so the log shows up in `links({ kind: "backlinks" })` for those docs. A bare path string (`Files touched: foo/bar.md`) does not register in the doc graph. The audit trail compounds only when the log is a real linker.

<!-- Example entry shape:

## YYYY-MM-DD: <short title>

- <what was done>
- Files touched: [path/to/doc-a](./path/to/doc-a.md), [path/to/doc-b](./path/to/doc-b.md)
- Sources ingested: [source-slug](./external-sources/source-slug.md)
- Open follow-ups: <topic-1>, <topic-2>

-->



## 2026-06-02: Populated KB — impending tech IPOs (OpenAI, Anthropic, SpaceX) + the AI capital web

- Researched IPO outlook + capital flows and wrote provisional profiles: [OpenAI](./research/openai.md), [Anthropic](./research/anthropic.md), [SpaceX](./research/spacex.md).
- Built the [AI capital-web funding chart](./research/ai-funding-web.md) — a themed bubble chart (circles sized by market value), a typed-edge relationship diagram (Bloomberg-style colored arrows), and the underlying node/edge dataset.
- Sources ingested: [openai-122b-funding-round](./external-sources/openai-122b-funding-round.md), [openai-nvidia-10gw-partnership](./external-sources/openai-nvidia-10gw-partnership.md), [openai-amd-6gw-partnership](./external-sources/openai-amd-6gw-partnership.md), [openai-oracle-300b-stargate](./external-sources/openai-oracle-300b-stargate.md), [openai-broadcom-10gw-accelerators](./external-sources/openai-broadcom-10gw-accelerators.md), [microsoft-openai-pbc-restructuring](./external-sources/microsoft-openai-pbc-restructuring.md), [openai-coreweave-contracts](./external-sources/openai-coreweave-contracts.md), [openai-infrastructure-1-15-trillion](./external-sources/openai-infrastructure-1-15-trillion.md), [anthropic-series-h-65b](./external-sources/anthropic-series-h-65b.md), [anthropic-amazon-compute](./external-sources/anthropic-amazon-compute.md), [anthropic-google-tpu-deal](./external-sources/anthropic-google-tpu-deal.md), [spacex-ipo-s1-filing](./external-sources/spacex-ipo-s1-filing.md), [market-caps-may-2026](./external-sources/market-caps-may-2026.md), [bloomberg-ai-circular-financing-chart](./external-sources/bloomberg-ai-circular-financing-chart.md).
- Preservation note: text sources captured as `text-extracted` (WebFetch would not reproduce full verbatim and `curl` was sandbox-blocked); the Bloomberg reference chart captured as `binary`.
- Open follow-ups: refresh live AMD / CoreWeave market caps; watch for OpenAI & Anthropic IPO filings; reconcile SpaceX's ~$1.25T (Feb-2026 xAI merger) vs ~$1.75T (IPO target) valuations; split firm vs. contingent compute commitments.
