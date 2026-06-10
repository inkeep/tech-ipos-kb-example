---
title: Which IPO Topics Are Trending on Hacker News — June 2026
description: "A trailing-31-day snapshot of IPO discussion on Hacker News (retrieved 2026-06-10): SpaceX dominates, the OpenAI/Anthropic AI-lab race follows, and the tone skews skeptical — valuations, S&P index inclusion, and retail access. Ranked by HN points/comments via the Algolia API."
status: provisional
date: 2026-06-10
tags:
  - report
  - snapshot
  - hacker-news
  - ipo
  - trends
  - spacex
  - openai
  - anthropic
author: Heegun Eom
---
> [!CAUTION]
> **Not financial advice.** This is a demonstration project. Figures and rankings here are a point-in-time scrape of public Hacker News data and may be provisional, incomplete, or quickly stale. See the [README disclaimer](../README.md) for full context.

# Which IPO Topics Are Trending on Hacker News — June 2026

**Author:** Heegun Eom · **Reporting window:** ~10 May – 10 June 2026 (trailing 31 days) · **Retrieved:** 2026-06-10 · **Source:** [Hacker News Search (Algolia) API](#methodology--sources)

> [!NOTE]
> **The headline: it's a mega-IPO summer, and Hacker News is fixated on SpaceX.** Across the trailing month, `IPO`-tagged story submissions are overwhelmingly about three private giants going public at once — **SpaceX, OpenAI, and Anthropic** — with SpaceX alone accounting for more story volume than every other IPO topic combined. The tone skews **skeptical**: the most-discussed threads question valuations, index-inclusion mechanics, and retail access rather than celebrating the listings.

## At a glance

```html preview
<div style="font-family:system-ui,sans-serif;padding:20px">
  <div id="cards" style="display:flex;gap:14px;flex-wrap:wrap"></div>
  <script>
    var stats = [
      ['IPO stories (trailing 31d)', '~790', 'HN story submissions', 'var(--chart-1)'],
      ['Top thread', '1,059 pts', '515 comments', 'var(--chart-2)'],
      ['SpaceX share of IPO chatter', '~60%', '132 of ~220 named stories', 'var(--chart-3)'],
      ['Dominant sentiment', 'Skeptical', 'valuation + access doubts', 'var(--chart-5)']
    ];
    document.getElementById('cards').innerHTML = stats.map(function (s) {
      return '<div style="flex:1;min-width:170px;padding:16px;background:var(--card);' +
        'color:var(--card-foreground);border:1px solid var(--border);' +
        'border-radius:var(--radius)">' +
        '<div style="font-size:13px;color:var(--muted-foreground)">' + s[0] + '</div>' +
        '<div style="font-size:24px;font-weight:700;margin-top:4px">' + s[1] + '</div>' +
        '<div style="font-size:12px;font-weight:600;margin-top:4px;color:' + s[3] + '">' +
        s[2] + '</div>' +
        '</div>';
    }).join('');
  </script>
</div>
```

## Topic share — story volume by IPO subject

Number of HN story submissions in the window whose title pairs a company with "IPO" (`<company> IPO`, story tag, trailing 31 days). SpaceX dwarfs the field.

```html preview
<div style="font-family:system-ui,sans-serif;padding:20px;color:var(--foreground)">
  <h3 style="margin:0 0 14px;font-size:15px;font-weight:600">HN IPO stories by subject (trailing 31 days)</h3>
  <div id="bars" style="display:flex;align-items:flex-end;gap:14px;height:200px"></div>
  <script>
    var data = [['SpaceX', 132], ['OpenAI', 42], ['Anthropic', 41], ['Bending Spoons', 7], ['Notion', 5], ['Perplexity', 2]];
    var max = Math.max.apply(null, data.map(function (d) { return d[1]; }));
    document.getElementById('bars').innerHTML = data.map(function (d, i) {
      return '<div style="flex:1;display:flex;flex-direction:column;align-items:center;' +
        'gap:6px;height:100%;justify-content:flex-end">' +
        '<span style="font-size:12px;font-weight:600">' + d[1] + '</span>' +
        '<div style="width:100%;height:' + (d[1] / max * 100) + '%;' +
        'background:var(--chart-' + (i % 5 + 1) + ');' +
        'border-radius:var(--radius) var(--radius) 0 0"></div>' +
        '<span style="font-size:11px;color:var(--muted-foreground);text-align:center">' + d[0] + '</span>' +
        '</div>';
    }).join('');
  </script>
</div>
```

*Counts are title-keyword matches via the Algolia API and approximate (a story titled "Sam Altman…ahead of OpenAI's IPO" counts toward OpenAI). They measure submission volume, not necessarily front-page reach.*

## The five themes driving the conversation

Reading the highest-scoring threads, the IPO discussion clusters into five recurring angles — and notably, most are **critical** rather than promotional.

### 1. Valuation skepticism — "is it worth that?"

The single loudest theme. Threads repeatedly argue the mega-IPOs are priced far above fair value, anchored on SpaceX's ~$1.78T target.

- [We Think the SpaceX IPO Is Overvalued](https://news.ycombinator.com/item?id=48455233) — 259 pts, 282 comments
- [Morningstar values SpaceX at $780B, half its IPO target](https://news.ycombinator.com/item?id=48373909) — 211 pts, 197 comments
- [The SpaceX IPO will be the theft of the century](https://news.ycombinator.com/item?id=48394034) — 142 pts, 120 comments
- [SpaceX's IPO is a disaster waiting to happen for your pension fund](https://news.ycombinator.com/item?id=48385866) — 92 pts

### 2. Index-inclusion mechanics — the surprise top story

The **most-upvoted IPO thread of the month** wasn't about a company at all — it was about whether these giants get fast-tracked into the S&P 500, and what forced index buying would mean for ordinary 401(k) holders.

- [SpaceX, Other Mega IPOs Denied Fast Index Entry by S&P](https://news.ycombinator.com/item?id=48405718) — **1,059 pts, 515 comments** (#1 of the window)
- [Ask HN: What is your opinion on index rule changes to accommodate Mega-Cap IPOs?](https://news.ycombinator.com/item?id=48368083) — 18 pts
- [Mega-cap IPOs: Implications for institutional investors and index managers](https://news.ycombinator.com/item?id=48422073)

### 3. Retail access & the "selling dreams" critique

An unusual amount of discussion about *who gets to buy in* — brokerages lowering minimums, and skepticism that retail is being sold the top.

- [Fidelity lowers SpaceX IPO entry requirement from $500,000 to just $2,000](https://news.ycombinator.com/item?id=48404734) — 23 pts
- [SpaceX IPO video sells Musk's space, AI, asteroid dreams to mom-n-pop investors](https://news.ycombinator.com/item?id=48408668)
- [China, HK Investors Banned from SpaceX IPO over Security](https://news.ycombinator.com/item?id=48412690)

### 4. The AI-lab IPO race & bubble fears

The through-line connecting the labs: a coordinated rush to public markets, shadowed by [AI "circular financing"](../articles/ai-capital-web.md) anxiety.

- [OpenAI Is Preparing to File for an IPO Soon](https://news.ycombinator.com/item?id=48210226) — 206 pts, 407 comments
- [Sam Altman's Business Dealings Under GOP Scrutiny Ahead of OpenAI's IPO](https://news.ycombinator.com/item?id=48134429) — 199 pts
- [Anthropic Is Preparing for IPO and We Should Be Worried](https://news.ycombinator.com/item?id=48193111) — 89 pts, 96 comments
- [Cheap AI Could Derail OpenAI and Anthropic's IPOs](https://news.ycombinator.com/item?id=48242934) — 13 pts
- [Fear of AI bubble ahead of SpaceX IPO](https://news.ycombinator.com/item?id=48459459)

### 5. Process explainers & "beyond the big three"

A quieter, more neutral strand: how IPOs actually work, plus the smaller names filing in the slipstream of the giants.

- [The mechanics of the IPO process (explained by a former Reddit CEO)](https://news.ycombinator.com/item?id=48457397)
- [Italy's Bending Spoons, owner of AOL and Vimeo, files for Nasdaq IPO](https://news.ycombinator.com/item?id=48446310) — 122 pts, 111 comments
- [Notion Names First Board of Directors in Key Step Toward IPO](https://news.ycombinator.com/item?id=48455176)
- [Perplexity plans IPO in 2028 regardless of what happens to Anthropic or OpenAI](https://news.ycombinator.com/item?id=48458991)

## Top 10 IPO threads of the month (by points)

| Pts | Comments | Date | Story | Subject |
| ---: | ---: | --- | --- | --- |
| 1,059 | 515 | Jun 4 | [SpaceX, Other Mega IPOs Denied Fast Index Entry by S&P](https://news.ycombinator.com/item?id=48405718) | Index mechanics |
| 259 | 282 | Jun 9 | [We Think the SpaceX IPO Is Overvalued](https://news.ycombinator.com/item?id=48455233) | SpaceX |
| 211 | 197 | Jun 2 | [Morningstar values SpaceX at $780B, half its IPO target](https://news.ycombinator.com/item?id=48373909) | SpaceX |
| 206 | 407 | May 20 | [OpenAI Is Preparing to File for an IPO Soon](https://news.ycombinator.com/item?id=48210226) | OpenAI |
| 199 | 163 | May 14 | [Sam Altman's Dealings Under GOP Scrutiny Ahead of OpenAI's IPO](https://news.ycombinator.com/item?id=48134429) | OpenAI |
| 142 | 120 | Jun 4 | [The SpaceX IPO will be the theft of the century](https://news.ycombinator.com/item?id=48394034) | SpaceX |
| 137 | 3 | May 21 | [OpenAI to confidentially file for IPO as soon as Friday](https://news.ycombinator.com/item?id=48217052) | OpenAI |
| 122 | 111 | Jun 8 | [Bending Spoons (AOL/Vimeo) files for Nasdaq IPO](https://news.ycombinator.com/item?id=48446310) | Bending Spoons |
| 92 | 48 | Jun 3 | [SpaceX's IPO is a disaster for your pension fund](https://news.ycombinator.com/item?id=48385866) | SpaceX |
| 89 | 96 | May 19 | [Anthropic Is Preparing for IPO and We Should Be Worried](https://news.ycombinator.com/item?id=48193111) | Anthropic |

## Why now — the backdrop

Three of the most valuable private companies in the world are listing within weeks of each other, which is why HN can't stop talking about it. The knowledge base already profiles each in depth:

- **[SpaceX](../research/spacex.md)** — ~$1.75T target, fixed $135/share (ticker SPCX); the dominant HN topic by far.
- **[OpenAI](../research/openai.md)** — $852B valuation, confidential S-1 filed; the AI-lab story HN debates most heatedly.
- **[Anthropic](../research/anthropic.md)** — $965B post-Series-H, confidential draft S-1 with the SEC.
- **[Other 2026 tech IPOs](../research/other-2026-ipos.md)** — the wider class (Bending Spoons, Cerebras, Notion, and the pipeline) that HN covers in the giants' slipstream.

The recurring skepticism on HN — overvaluation, forced index buying, retail being sold the top — maps directly onto the [AI capital-web](../articles/ai-capital-web.md) "circular financing" concern and the historical base rate that [most IPOs underperform over five years](../research/post-ipo-performance.md).

## Methodology & sources

- **Data source:** the public [Hacker News Search (Algolia) API](https://hn.algolia.com/api) — `https://hn.algolia.com/api/v1/search` (relevance) and `/search_by_date` (recency).
- **Query:** `query=IPO` (plus per-subject `"<company> IPO"` queries), `tags=story`, `numericFilters=created_at_i>` the timestamp 31 days before retrieval.
- **Window:** ~2026-05-10 → 2026-06-10. **Retrieved:** 2026-06-10.
- **Ranking metric:** HN `points` (net upvotes) and `num_comments`, as returned by Algolia at retrieval time. "Trending" here = submission volume + engagement on `IPO`-tagged stories; it is *not* a measure of front-page time.
- **Each row in the tables links to the original HN discussion thread** — the primary artifact this report observes.
- **Caveats:** title-keyword topic counts are approximate; comment/point totals are a snapshot and drift as threads age; the relevance endpoint caps returned hits, so totals (~790 stories) are lower-bound estimates. Market-valuation and filing facts cited in *Why now* are grounded in the linked research docs (e.g. [SpaceX](../research/spacex.md), [OpenAI](../research/openai.md), [Anthropic](../research/anthropic.md)), which carry their own external-source citations.

---

*A point-in-time HN trend snapshot. For the durable IPO analysis it draws on, see the [SpaceX](../research/spacex.md), [OpenAI](../research/openai.md), and [Anthropic](../research/anthropic.md) profiles and the [README](../README.md).*
