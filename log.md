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

## 2026-06-05: SpaceX IPO price set — fixed $135/share

- SpaceX is now targeting a **fixed $135/share** offer price (no range): ~555.6M shares ≈ ~$75B raised at ~$1.75T. Added the per-share price to the [SpaceX profile](./research/spacex.md) (snapshot, valuation trajectory, IPO mechanics, frontmatter) and refreshed now-stale "not priced / moving target" language in [README](./README.md) and [Historical tech IPOs](./research/historical-tech-ipos.md).
- Sources ingested: [spacex-ipo-135-price](./external-sources/spacex-ipo-135-price.md) (CNBC citing Reuters, cross-referenced with TECHi S-1/A breakdown).
- Preservation note: captured `text-extracted` (CNBC WebFetch returned 403; figures cross-referenced from TECHi).
- Open follow-ups: confirm $135 against the effective prospectus / pricing notice once filed; watch the June 11 pricing → June 12 listing; refresh post-IPO performance tracking after SPCX debuts.



## 2026-06-02: Added historical tech-IPO chart (by year)

- Researched the largest tech IPO per year (1995–2026) and wrote [Historical Tech IPOs by Year](./research/historical-tech-ipos.md) — a themed capital-raised bar chart placing the 2026 cohort (esp. SpaceX's ~$75B target) against past records (Alibaba $21.8B, Facebook $16B, Rivian $11.9B, Uber $8.1B, Snowflake $3.4B, Google $1.67B, Netscape $0.14B), plus a by-year dataset table.
- Sources ingested (`curl`, now that the sandbox is disabled): [cnbc-biggest-tech-ipos-2020](./external-sources/cnbc-biggest-tech-ipos-2020.md), [historical-tech-ipo-figures](./external-sources/historical-tech-ipo-figures.md).
- Cross-linked the new chart from [SpaceX](./research/spacex.md) and [the AI capital web](./research/ai-funding-web.md).
- Open follow-ups: confirm SpaceX's final raise at pricing (~$30B vs ~$75B reports); optionally add an IPO-day-valuation chart and a direct-listings view.



## 2026-06-04: Added KB landing page (README)

- Created [README](./README.md) as the front door — the KB had no introductory/overview page. Covers the subject (2026 mega-IPOs: SpaceX, OpenAI, Anthropic + the AI capital web), a "where to start" list pointing at the [funding chart](./research/ai-funding-web.md) and [historical IPO chart](./research/historical-tech-ipos.md), and a map of the ingest→research→consolidate layer structure.
- No new sources or claims beyond what the linked research docs already cite; purely navigational. Verified zero dead links.



## 2026-06-05: Anthropic IPO filing — ingested source + propagated to research and README

- Anthropic confidentially filed a draft Form S-1 with the SEC on **Jun 1, 2026**. Ingested the primary [Rule 135 announcement](./external-sources/anthropic-confidential-s1.md) (anthropic.com), cross-checked against CNBC / TechCrunch / NPR reporting.
- Updated [Anthropic research profile](./research/anthropic.md): snapshot + IPO-outlook status changed from "no filing yet" to filed; refreshed the open question; added the announcement to `sources:`.
- Updated [README](./README.md): Anthropic table row + intro line now reflect that all three anchors (SpaceX, OpenAI, Anthropic) have filed.
- Note: OpenAI's confidential filing was already reflected in the KB; this turn only adds Anthropic. Verified zero dead links.
- Resolves the prior follow-up "watch for OpenAI & Anthropic IPO filings." Remaining: shares/price/timing not yet set for any of the three; SpaceX final raise still unconfirmed at pricing.



## 2026-06-05: Added "Other 2026 Tech IPOs" survey — beyond the big three

- Answered "are there other 2026 IPOs besides SpaceX/OpenAI/Anthropic?" with a provisional survey: [Other 2026 Tech IPOs](./research/other-2026-ipos.md). Covers the one *completed* large tech IPO (Cerebras) plus the filed/expected pipeline (Databricks, Stripe, Canva, Cohere, Strava, Lime), and how the AI capital web connects the whole class.
- Sources ingested: [Cerebras IPO 2026](./external-sources/cerebras-ipo-2026.md) (TechCrunch + CNBC/TechTimes cross-ref), [Built In 2026 IPO watchlist](./external-sources/builtin-2026-ipo-watchlist.md).
- Updated [README](./README.md): added an "Other 2026 Tech IPOs" link to "Where to start"; bumped source count (16→18) and research count (5→6).
- **Tooling note:** OK MCP write path was unavailable this turn (session tool index exposed `write_document`, which the running v0.10.0-beta.3 server rejects; the server's `write` tool was not reachable). Files authored via native tools under the skill's escape hatch — no CRDT agent attribution for these writes. Frontmatter shape, sourcing, and link integrity kept identical to existing docs.
- Open follow-ups: confirm which pipeline names actually price in 2026; reconcile Cerebras close-day valuation (~$66B vs ~$95B); consider adding Cerebras (OpenAI-as-customer) as a node/edge in the [AI capital web](./research/ai-funding-web.md).



## 2026-06-05: Added not-financial-advice / demonstration-only disclaimers

- Added a prominent `> [!CAUTION]` disclaimer to the [README](./README.md) front door (not financial/investment/legal/tax advice; example project; figures may be provisional, inaccurate, or fictional).
- Added a compact matching disclaimer callout (linking back to the README) to all six research docs: [ai-funding-web](./research/ai-funding-web.md), [anthropic](./research/anthropic.md), [historical-tech-ipos](./research/historical-tech-ipos.md), [openai](./research/openai.md), [spacex](./research/spacex.md), [other-2026-ipos](./research/other-2026-ipos.md).
- Scope note: `external-sources/` (raw third-party captures, already source-attributed) intentionally left without the disclaimer; can extend there if desired.
- Tooling: OK MCP write path worked this turn (index refreshed to polymorphic `write`/`edit`). Verified zero dead links across all edited docs.

## 2026-06-05: Added animated post-IPO performance chart (IPO day → 5 years)

- Built [Post-IPO Performance: the 2019–2021 Cohort](./research/post-ipo-performance.md) — a self-contained, themed `html preview` **animation** (SVG line-race) of Uber, Snowflake, and Rivian, each rebased to its IPO **offer price = 100**, played from IPO day out to the 5-year mark with a replay button, a months-since-IPO clock, and live per-company index labels. Intended as a demonstration of Open Knowledge's live interactive embeds.
- Sources ingested: [post-ipo-stock-performance-figures](./external-sources/post-ipo-stock-performance-figures.md) — IPO terms, first-day closes, post-IPO peaks, and calendar year-end closes (companiesmarketcap.com annual performance + IPO/peak/low pages; year-end closes cross-checked vs Yahoo Finance/Nasdaq; IPO terms from CNBC/Fortune).
- Cross-linked the new chart from [README](./README.md) (where-to-start) and [Historical Tech IPOs by Year](./research/historical-tech-ipos.md) (further reading). Verified zero dead links.
- Method note: plotted points are documented **anchors** (offer, day-1 close, peak, year-end closes) with the line interpolated between them — not a literal monthly close series; stated explicitly in the chart caveats. Each line runs to the company's real age, so Rivian (Nov 2021) stops near month 55.
- Open follow-ups: if a true month-end series is wanted, source full monthly closes per ticker; consider adding the 2026 cohort once any of them have post-IPO trading history.

## 2026-06-05: Reframed post-IPO chart as % return since IPO

- Reframed [Post-IPO Returns](./research/post-ipo-performance.md) per request: y-axis is now your **cumulative % return if you bought at the IPO offer price**, with a **0% breakeven baseline** (was an offer=100 index). Same underlying anchors; only the axis framing, labels, title, and captions changed. Updated link labels in [README](./README.md) and [Historical Tech IPOs by Year](./research/historical-tech-ipos.md) to match.

## 2026-06-05: Added Tesla benchmark + log/linear toggle to post-IPO returns chart

- Added **Tesla (2010 IPO)** as a fourth line on [Post-IPO Returns](./research/post-ipo-performance.md), as a scale benchmark (the generational winner: ~+1,460% by year 5 vs the recent cohort's −80%…+40%). Because Tesla dwarfs the others, added an interactive **Log / Linear y-axis toggle** so all four stay readable on log, while linear shows the true magnitude gap.
- Ingested Tesla figures into the [post-IPO reference](./external-sources/post-ipo-stock-performance-figures.md): IPO $17 (Jun 29 2010), day-1 close $23.89 (+40.5%), nominal year-end closes (2013 $150.43, 2014 $222.41) with split-adjusted reconciliation (15:1 total; returns split-invariant). Sources: companiesmarketcap annual performance, Tesla IR pricing release, CNBC.
- Note: Tesla is deliberately *not* in the 2019–2021 cohort — flagged as a benchmark in-chart and in caveats. Zero dead links.

## 2026-06-05: Added average + median all-IPO benchmark lines (Ritter data)

- Answered "what about average returns on IPOs outside our set" by adding two dashed benchmark lines to [Post-IPO Returns](./research/post-ipo-performance.md): the **average (mean)** and **typical (median)** U.S. IPO, equal-weighted buy-and-hold from the offer price. The mean ends ~+57% at 5yr; the median is ~−22% — the dispersion (skew from a few moonshots) is the headline, and ~56% of IPOs lose money over 3 years.
- Ingested [Ritter IPO long-run returns](./external-sources/ritter-ipo-long-run-returns.md) — text-extracted key tables (20-1 event-year returns, 16e mean/median BHR + distribution, 16f from-offer BHR, first-day pop) from Jay Ritter's *Updated Long-run Statistics* (Univ. of Florida, Apr 2026). Binary PDF preservation was attempted but the asset upload returned a server error, so fell back to the project's text-extracted pattern with source_url.
- Added a mean-vs-median stat table + framing to the chart doc. Verified zero dead links.

## 2026-06-05: Fixed broken edge-color legend in the AI capital web

- Fixed a non-rendering passage in [AI capital-web funding chart](./research/ai-funding-web.md): the "Edge colors" legend was raw inline `<span style="color:#hex">` HTML, which fails under MDX/JSX rendering (JSX `style` must be an object, not a string) and hardcoded off-theme hex colors.
- Replaced it with a themed `html preview` legend wired to theme tokens (green=`--chart-2`, blue=`--chart-1`, amber-dashed=`--chart-3`), matching the doc's existing bubble-chart palette. No content/data changed — same three edge-type semantics.
- Open follow-ups: the relationship web is still legend-only; a typed-edge diagram (mermaid or `html preview`) could make the green/blue/amber flows visible rather than just described.

## 2026-06-05: Added mermaid recreation of the typed funding web

- Recreated the funding web as a `mermaid` directed graph in [AI capital-web funding chart](./research/ai-funding-web.md), under the relationship-web legend: 12 entity nodes (labels carry market value / valuation) and 18 typed edges built from the doc's edge dataset — green = investment, blue = compute purchase, amber-dotted = equity / warrant / backstop. The three impending-IPO labs are border-highlighted. Verified it renders in the preview (12 nodes / 18 edges, no error).
- Gotcha worth remembering: this renderer's mermaid `linkStyle` / `classDef` grammar rejects `var(--token)` (parse error on the `(`). Unlike `html preview` embeds, mermaid edge colors must be literal (hex). Used literal green/blue/amber for edges; kept node styling theme-aware by highlighting labs with a token-free `stroke-width` bump only.
- Open follow-ups: edge colors are fixed hex (can't track theme) — acceptable since they're semantic, but a fully theme-tracking version would need an `html preview` SVG instead of mermaid.

## 2026-06-05: Added public-demo-repo framing + Open Knowledge links to README

- Reframed [README](./README.md) so the **"this is a public demo repository"** fact is front-and-center for outside readers landing via GitHub: added an `IMPORTANT` banner explaining the repo is a public example built with Open Knowledge and safe to share, and trimmed the existing `CAUTION` block to focus on the financial-disclaimer angle (no longer double-stating "demonstration project").
- Added a **"Built with Open Knowledge"** section near the foot, both banner and footer linking to the Open Knowledge documentation (`github.com/inkeep/open-knowledge`, Inkeep's agent-native, local-first markdown-CRDT platform). Verified the canonical repo URL against npm + GitHub (npm `homepage` still points at the `-legacy` repo; `github.com/inkeep/open-knowledge` is the current project).
- No knowledge-base content changed; only repo-meta framing. Zero dead internal links.
