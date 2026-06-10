---
title: Hacker News IPO Story Search — June 2026 Algolia Extract
description: HN Algolia story-search extract for IPO-related posts created June
  1-10, 2026 UTC, with false-positive filtering and topic-level engagement
  aggregates.
source_url: https://hn.algolia.com/api/v1/search?query=IPO&tags=story&numericFilters=created_at_i%3E%3D1780272000,created_at_i%3C1781136000&hitsPerPage=100
media_type: application/json
date_fetched: 2026-06-10
author: Hacker News Algolia API / extracted by Codex
preservation: data-extracted
tags:
  - source
  - immutable
  - layer-ingest
  - hacker-news
  - ipo
  - trends
---
## Capture

This source preserves the June 2026 Hacker News story-search evidence used to identify IPO topics that were active on HN this month.

| Field | Value |
| --- | --- |
| API | HN Algolia story search |
| Query | `IPO` |
| Tag filter | `story` |
| Date window | `created_at_i >= 1780272000` and `< 1781136000` = June 1-10, 2026 UTC |
| Pages fetched | 0-5 (`hitsPerPage=100`) |
| Raw API hit count | 519 |
| Cleaned IPO-story count | 87 |
| False-positive filter | Removed non-IPO matches such as IOCCC, iPod, `ipotapov`, and `draft-cruzgonzalez-ipoac-dns` |
| Engagement metric | HN points + HN comments |

## Topic aggregates

Stories can count toward more than one company/topic when the same HN item names multiple IPO candidates.

| Topic | Matching stories | HN points | HN comments | Engagement |
| --- | ---: | ---: | ---: | ---: |
| SpaceX | 58 | 2,246 | 1,441 | 3,687 |
| Anthropic | 18 | 760 | 619 | 1,379 |
| Bending Spoons | 4 | 131 | 112 | 243 |
| OpenAI | 8 | 70 | 7 | 77 |
| Perplexity | 1 | 5 | 0 | 5 |
| StepFun | 1 | 5 | 0 | 5 |
| Strava | 1 | 4 | 1 | 5 |
| Notion | 1 | 2 | 0 | 2 |

## Highest-engagement rows

| HN item | Created | Points | Comments | Engagement | Title | Topic signal |
| --- | --- | ---: | ---: | ---: | --- | --- |
| 48405718 | 2026-06-04 | 1,059 | 515 | 1,574 | SpaceX, Other Mega IPOs Denied Fast Index Entry by S&P | SpaceX / mega-cap index rules |
| 48358646 | 2026-06-01 | 530 | 451 | 981 | Anthropic confidentially submits draft S-1 to the SEC | Anthropic filing |
| 48455233 | 2026-06-09 | 260 | 282 | 542 | We Think the SpaceX IPO Is Overvalued | SpaceX valuation critique |
| 48373909 | 2026-06-02 | 211 | 197 | 408 | Morningstar values SpaceX at $780B, half its IPO target | SpaceX valuation critique |
| 48368187 | 2026-06-02 | 134 | 155 | 289 | Michael Burry says neither SpaceX nor Anthropic is worth $1T | SpaceX / Anthropic valuation critique |
| 48394034 | 2026-06-04 | 142 | 120 | 262 | The SpaceX IPO will be the theft of the century | SpaceX valuation critique |
| 48446310 | 2026-06-08 | 122 | 111 | 233 | Italy's Bending Spoons, owner of AOL and Vimeo, files for Nasdaq IPO | Bending Spoons filing |
| 48385866 | 2026-06-03 | 92 | 48 | 140 | SpaceX's IPO is a disaster waiting to happen for your pension fund | SpaceX risk critique |
| 48414582 | 2026-06-05 | 24 | 42 | 66 | Ask HN: Are orbital data centers possible / a good idea? | SpaceX orbital-compute thesis |
| 48391046 | 2026-06-03 | 29 | 7 | 36 | We Uncovered a Hidden Wealth Transfer in the SpaceX IPO. You're Holding the Bag [video] | SpaceX valuation critique |
| 48404734 | 2026-06-04 | 23 | 5 | 28 | Fidelity lowers SpaceX IPO entry requirement from $500,000 to just $2,000 | SpaceX retail-access mechanics |
| 48359035 | 2026-06-01 | 26 | 2 | 28 | Anthropic Files to Go Public, Setting Stage for Huge I.P.O. | Anthropic filing |
| 48452224 | 2026-06-08 | 24 | 1 | 25 | OpenAI Confidentially Files for IPO | OpenAI filing |
| 48369063 | 2026-06-02 | 23 | 2 | 25 | Elon Musk Laid Out 602 Goals. We Counted How Many He Hit | SpaceX / Musk execution risk |
| 48436328 | 2026-06-07 | 20 | 1 | 21 | Musk's SpaceX IPO Narrative Is a Whole New Level of Bullshit | SpaceX valuation critique |
| 48468135 | 2026-06-09 | 11 | 6 | 17 | SpaceX IPO demand is approaching four times oversubscribed | SpaceX demand |
| 48466828 | 2026-06-09 | 7 | 10 | 17 | Ask HN: Prediction for SpaceX IPO? | SpaceX prediction thread |
| 48390904 | 2026-06-03 | 16 | 0 | 16 | SpaceX Sets Price for $1.77T IPO | SpaceX pricing |
| 48461028 | 2026-06-09 | 4 | 12 | 16 | Ask HN: Will you invest in SpaceX IPO? | SpaceX retail-interest thread |
| 48390292 | 2026-06-03 | 13 | 0 | 13 | SpaceX wins Texas tax breaks for chip project, ahead of record IPO | SpaceX / chip project |
| 48451099 | 2026-06-08 | 12 | 1 | 13 | Why Morningstar believes the SpaceX IPO is overvalued | SpaceX valuation critique |
| 48384932 | 2026-06-03 | 10 | 3 | 13 | Anthopic, OpenAI Should Not Be Allowed to IPO, Says Ed Zitron [video] | Anthropic / OpenAI critique |

## Low-signal IPO mentions

The same cleaned data found one-story, five-or-fewer-engagement mentions for Perplexity, StepFun, Strava, and Notion. Those mentions are useful watchlist signals but do not meet the report's threshold for a trending topic.