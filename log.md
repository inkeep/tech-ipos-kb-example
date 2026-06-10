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
- Files touched: `path/to/doc-a`, `path/to/doc-b`
- Sources ingested: `source-slug`
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

## 2026-06-05: Added a live TSLA ticker as an html-preview embed

- Built **Live TSLA Ticker** (`research/tsla-live-ticker.md`, since removed) — a self-contained, themed `html preview` widget that fetches **real close-of-day** Tesla quotes and renders a ticker card (price, day-over-day change, prev close, open, day range, 52-week range) with a status indicator and a manual Refresh; auto-polls every 60s.
- **No API key in the repo** (per request): reads Yahoo Finance's public chart endpoint through a keyless, CORS-friendly proxy (`api.allorigins.win`, fallback `api.codetabs.com`). Day-over-day change is computed against the prior trading day's close from the daily-close series (avoids Yahoo's `chartPreviousClose`, which is the range-start close); open is read from the latest daily candle. Every color is a theme token (green=`--chart-2`, red=`--destructive`); degrades to *Data unavailable — retrying…* when both proxies are rate-limited.
- Cross-linked from [README](./README.md) (where-to-start). Verified zero dead links.
- Verification note: the fetch+proxy+parse logic was confirmed working in a standalone browser this session (rendered live: $391.00, −6.56% vs prior close). Could **not** visually confirm it inside OK's live preview this session — the preview pane returned intermittent 502s and didn't render doc bodies, so the open question of whether OK's `html preview` iframe sandbox permits the cross-origin fetch is unverified in-app.
- Caveat: public CORS proxies are best-effort (demo-grade, not production); "live" = last close, not streaming intraday.
- Open follow-ups: confirm the live fetch renders in the OK preview iframe (sandbox/CSP `connect-src`); if blocked, consider a same-origin data shim or a static snapshot fallback. Optionally parameterize the symbol.

## 2026-06-05: First canonical article — the AI capital web

- Populated the previously-empty `articles/` (consolidate) layer with its first canonical entry: [The AI Capital Web — Canonical Reference](./articles/ai-capital-web.md). Instantiated from the folder's `article` template, then filled it: a stable source-of-truth *framing* of the capital web — the three edge types (investment / compute purchase / equity-warrant), the anchor nodes, the mermaid web diagram, and the canonical definition of "circular financing."
- Marked it `status: canonical` with `supersedes: [research/ai-funding-web.md]` — the article owns the framing; the provisional [research doc](./research/ai-funding-web.md) keeps the volatile detail (snapshot valuations, full node/edge dataset, per-deal sources). The evidence chain stays traceable: article → research → `external-sources/`.
- Linked it from [README](./README.md) (replaced the stale "Articles — none yet" note), so the demo now shows all three Karpathy layers populated. Verified zero dead links in the new article.
- Note: this was a demonstration of the consolidate *mechanism* (template → canonical → supersedes chain), not a new market claim — the canonical content is descriptive and rests entirely on existing research.
- Open follow-ups: none — keep the article stable; update only when a new decision supersedes it.

## 2026-06-05: TSLA ticker — OK embeds block live fetch (CSP), switched to snapshot

- Followed up on the live-ticker attempt: verified in the OK preview that every `html preview` embed iframe carries a Content-Security-Policy with **`connect-src 'none'`** (alongside `sandbox="allow-scripts"`). That blocks all `fetch`/XHR/WebSocket from inside an embed — so a render-time *live* ticker is **not possible** in an OK embed by design (embeds are sandboxed to be self-contained, like the [animated returns chart](./research/post-ipo-performance.md)). The proxy was healthy (allorigins 200); the data was blocked at the CSP layer, confirmed by reading the injected `<meta http-equiv="Content-Security-Policy">` in the iframe srcdoc.
- Rebuilt **TSLA Ticker** (`research/tsla-live-ticker.md`, since removed) as a **CSP-safe close-of-day snapshot**: real Yahoo Finance figures (TSLA $391.00, −6.56% vs prior close; prev $418.45, open $420.55, day 388.59–424.68, 52w 273.21–498.83, as of 2026-06-05) baked into the themed card (green=`--chart-2`, red=`--destructive`). Verified it renders correctly in the OK preview. Documented the `connect-src 'none'` boundary and the “refresh on a schedule” pattern in-doc.
- The truly-live version remains the standalone `examples/tsla-ticker.html` (a plain browser page has no such CSP; polls Yahoo via a keyless CORS proxy every 60s) — noted in the doc as the out-of-KB option.
- Updated [README](./README.md) blurb to match (snapshot embed, not live widget). Verified zero dead links.
- Open follow-ups: optionally wire a daily scheduled agent to re-pull the close and rewrite the embed after U.S. market close; optionally parameterize the symbol.

## 2026-06-05: Scrapped the TSLA ticker — live data not feasible in an OK embed

- Removed the TSLA ticker work. Conclusion: a self-updating *live* ticker isn't possible **inside** an OK `html preview` embed — the iframe's CSP sets `connect-src 'none'`, so no `fetch`/XHR/WebSocket. The only ways to make it move are an external scheduled rewrite (CRDT-streamed into the preview) or fake/simulated motion; the user opted not to pursue either for now.
- Deleted `research/tsla-live-ticker.md`; removed its link from [README](./README.md) (where-to-start) and de-linked the two prior log references above (doc no longer exists). Also removed `examples/refresh-tsla.py` and reverted the `examples-static` static-server entry in `.claude/launch.json`.
- Kept the durable learning in agent memory (OK embeds run under `connect-src 'none'` — bake data in or refresh on a schedule) so we don't re-discover it. Verified zero dead links.

## 2026-06-08: Restored the TSLA ticker as a live-vs-static failure analysis

- Brought back [TSLA Ticker — why the live version fails](./research/aapl-live-ticker.md), reframed as a forensic analysis of *why* a live ticker can't work in an OK `html preview` embed and *why* a static render was the only option that shows data.
- The doc holds **two embeds side by side**: (A) a live-fetch attempt that **self-diagnoses** — it reads its own injected CSP and prints the cause, and (B) a static snapshot that renders fine. Verified live in the OK preview: panel A shows `TypeError: Failed to fetch`, `iframe origin: 'null' (opaque sandbox)`, and `CSP connect-src: connect-src 'none'`; panel B shows the green card ($409.75, +4.80%, as of 2026-06-08).
- Evidence re-measured this turn: Yahoo direct `curl` = **HTTP 200** (0.09s); `allorigins` proxy = **HTTP 522** (~20s, flaky red herring); in-embed `fetch()` = blocked before send. Root cause = OK injects `connect-src 'none'` (plus `img-src data:`, `frame-src 'none'`, etc.) into every embed iframe — a deliberate exfiltration guard.
- Re-linked from [README](./README.md) where-to-start. Verified zero dead links.

## 2026-06-08: TSLA analysis — went direct to Yahoo (dropped the proxy in panel A)

- Per request “can we go direct to the Yahoo API instead of the proxy.” Switched panel A of [the analysis](./research/aapl-live-ticker.md) to call `query1.finance.yahoo.com` **directly** (no allorigins). Verified live: it still fails with `TypeError: Failed to fetch` + `connect-src 'none'` — proving the proxy was never the in-embed blocker (the CSP blocks every destination).
- Added a **“going direct vs proxy”** section with a three-case truth table: in-embed (✕ CSP blocks all), standalone browser (✕ Yahoo sends no `Access-Control-Allow-Origin`), server-side (✓ go direct). Evidence this turn: cross-origin request to Yahoo returns **no `access-control-*` headers**; server-side `curl` returns **HTTP 200**.
- Net: the proxy only ever existed as a browser-CORS shim; the live-refresh path (server-side) should and does go straight to Yahoo. Zero dead links.

## 2026-06-10: Updated SpaceX profile with latest IPO news (pre-listing)

- Refreshed [SpaceX](./research/spacex.md) ahead of the imminent ~Jun 12 listing. Added a new **"Latest developments (as of Jun 10, 2026)"** section and threaded the news into the snapshot, risks, and open questions: book **~4× oversubscribed** (Reuters, Jun 9); **S&P Dow Jones declined to fast-track** mega-cap IPOs into the S&P 500 (Bloomberg, Jun 4 — the #1 HN IPO story, 1,059 pts), so **no automatic index-fund buying** at debut; **Morningstar ~$780B fair value** (~half the ~$1.78T target), plus Burry and Eisman skepticism; **China/HK barred** from the offering.
- **Grounding:** the live outlet pages (Reuters/Bloomberg/Morningstar) are paywalled/blocked to WebFetch, so claims are cited to the already-ingested [HN Algolia extract](./external-sources/hacker-news-ipo-algolia-june-2026.md) (real captured data — headlines, dates, outlets, engagement) rather than fabricating new source bodies. Added that extract to the doc's `sources:` and bumped `date` to 2026-06-10.
- Verified zero dead links.
- Added a themed **valuation-gap chart** (`html preview`): IPO target ~$1.78T vs Morningstar fair value ~$780B (~2.3× / ~$1.0T gap), wired to theme tokens, in a new "The valuation gap" subsection.
- Open follow-ups: after SPCX prices/lists, capture the actual offer outcome + day-1 trade and ingest a primary pricing source; revisit Morningstar's ~$780B vs the market once it trades.

## 2026-06-10: Added HN IPO-trends report (new reports/ layer)

- Answered "which IPO topics are trending on Hacker News this month" with a point-in-time snapshot: [Which IPO Topics Are Trending on Hacker News — June 2026](./reports/hacker-news-ipo-trends-2026-06.md). Headline: it's a mega-IPO summer and HN is fixated on **SpaceX** (~60% of named IPO story volume), followed by the **OpenAI/Anthropic** AI-lab race; tone skews **skeptical** (valuations, S&P index inclusion, retail access).
- Created a new **`reports/`** folder (with frontmatter) for time-boxed trend snapshots — distinct from `research/` (per-subject profiles) and `articles/` (canonical). The report carries a themed stat-card row + a topic-share `html preview` bar chart, a top-10 threads table, a five-theme breakdown, and an inline **Methodology** section.
- **Data/grounding:** live scrape of the public Hacker News (Algolia) Search API — `query=IPO`, `tags=story`, trailing-31-day window, retrieved 2026-06-10, ranked by points/comments. Every story row links to its HN discussion thread (the primary artifact); market-fact claims in *Why now* cross-link to existing [research](./research/spacex.md) docs that carry external-source citations. No new `external-sources/` captured (the report observes HN itself, not a synthesized claim set).
- Cross-linked from [README](./README.md) where-to-start. Verified zero dead links; corrected several HN thread permalinks that initially shared a placeholder item id.
- Open follow-ups: refresh after SPCX lists (~June 12) to capture post-debut reaction; optionally automate a recurring HN scan.

## 2026-06-09: Live ticker resolved — keyless + CORS + no proxy (Twelve Data demo, AAPL)

- Found the CORS-side half of the fix to pair with OK's relaxed embed CSP. Tested several quote APIs with a cross-origin `Origin` header: Finnhub / Twelve Data / Alpha Vantage / FMP **all send `Access-Control-Allow-Origin: *`** (Yahoo is the lone exception) — but need a key. **Twelve Data's public `demo` token returns a full quote for AAPL** (price / change / OHLC / prev close / 52-week) **keyless + CORS**; CoinGecko is keyless+CORS for crypto.
- Added **Panel C** to [the analysis](./research/aapl-live-ticker.md): a live AAPL ticker that fetches `api.twelvedata.com` **directly — no proxy, no managed key**. It prints the live `connect-src`, so it doubles as a verifier of the CSP rebuild (red `Blocked` under `connect-src 'none'`; live data under `connect-src https:`).
- Constraints documented in-doc: `demo` token = **AAPL only** (TSLA needs a free key = a key in a public repo); truly zero-token CORS feeds exist only for crypto (CoinGecko) / FX, not arbitrary equities.
- Data path proven by `curl` (Twelve Data demo+AAPL → full JSON + `ACAO: *`). In-embed live render is gated on the app rebuild that ships `connect-src https:` (the running build still served `'none'` at last check; preview churned during the dev restarts). Zero dead links.

## 2026-06-09: Live ticker CONFIRMED working in-embed (CSP rebuild landed)

- Restarted the preview; the fresh OK build now serves `connect-src https: wss: data: blob:` (the CSP fix is live). Panel C of [the analysis](./research/aapl-live-ticker.md) renders **live AAPL data fetched directly from `api.twelvedata.com`** — no proxy, no managed key: $301.54, −1.89%, prev $307.34, open $308.74, day 301.17–317.40, 52w 195.07–317.40, green “Live” + working Refresh. Footer confirms `direct → api.twelvedata.com · no proxy · connect-src https:`.
- Full arc closed: `connect-src 'none'` (blocked) → static snapshot (workaround) → relaxed CSP + a CORS-sending API (Twelve Data) = genuinely live, proxy-free, key-free embed.

## 2026-06-09: Renamed the ticker doc around the live AAPL example

- Renamed `research/tsla-live-ticker` → [research/aapl-live-ticker](./research/aapl-live-ticker.md) and reframed its title/description/tags around the **working live example (AAPL)** rather than TSLA — since the genuinely-live, keyless, proxy-free embed (Panel C) is AAPL. The move auto-rewrote inbound links in [README](./README.md) and the log.
- Body analysis panels A (direct-Yahoo live attempt) and B (static snapshot) keep TSLA as the historical “why the naive version failed” case; the title now frames the doc as the AAPL live ticker + that analysis. Verified zero dead links.

## 2026-06-10: Added HN IPO trends report for June 2026

- Created the canonical report [HN IPO Topics Trending This Month — June 2026](./articles/hn-ipo-trends-june-2026.md), ranking HN-active IPO topics from highest valuation to lowest: SpaceX, Anthropic, OpenAI, and Bending Spoons.
- Added the supporting provisional synthesis [HN IPO Trends — June 2026](./research/hn-ipo-trends-june-2026.md), including the trend threshold and engagement method.
- Sources ingested: [Hacker News IPO Story Search — June 2026 Algolia Extract](./external-sources/hacker-news-ipo-algolia-june-2026.md) and [Bending Spoons Files for U.S. IPO](./external-sources/bending-spoons-ipo-2026.md).
- Open follow-ups: consider adding Bending Spoons to [Other 2026 Tech IPOs](./research/other-2026-ipos.md); refresh the HN pull after OpenAI publishes a public S-1 or after SpaceX lists.

## 2026-06-10: Added Anthropic Fable use-case article

- Created the canonical article [What People Are Doing with Anthropic's Claude Fable 5](./articles/anthropic-fable-use-cases.md), covering early distinctive uses: Stripe's codebase migration, vision-only Pokemon FireRed gameplay, screenshot-to-code reconstruction, Ethan Mollick's Concord survey-analysis tool, his isochrone map, math-generated games, IMC trading-analysis reasoning, and long-memory game strategy.
- Added the supporting synthesis [Anthropic Fable Use Cases - Source Scan](./research/anthropic-fable-use-cases.md).
- Sources ingested: [Anthropic Announces Claude Fable 5 and Claude Mythos 5](./external-sources/anthropic-claude-fable-5-mythos-5.md), [Ethan Mollick on Working with Claude Fable / Mythos](./external-sources/ethan-mollick-fable-mythos-use-cases.md), and [Business Insider Tests Claude Fable 5 Safeguards](./external-sources/business-insider-fable-5-safeguards.md).
- Caveat captured in the article: public Fable 5 is newly launched and deliberately falls back on some cybersecurity, biology and chemistry, and distillation prompts, so trusted-access Mythos examples are treated as boundary cases rather than ordinary public Fable use.
