---
title: Ethan Mollick on Working with Claude Fable / Mythos
sdescription: Early-access writeup describing how Ethan Mollick used Claude Fable to build research tools, maps, games, and other long-horizon artifacts.
source_url: https://www.oneusefulthing.org/p/what-it-feels-like-to-work-with-mythos
media_type: text/html
date_fetched: 2026-06-10
author: Ethan Mollick, One Useful Thing
preservation: text-extracted
tags:
  - source
  - immutable
  - layer-ingest
  - text
  - anthropic
  - fable
  - mythos
  - claude
  - use-cases
---
## Extracted source notes

Ethan Mollick published an early-access account of working with Claude Fable on June 9, 2026. He describes Fable as the first Mythos-class model being released to the public and says he tested it on tasks outside cybersecurity because the Fable guardrails made cybersecurity work impractical.

Mollick reports that Fable could execute on multi-page specifications for up to about a dozen hours. He says it outperformed other public models he had used across many experiments, while also being expensive in token usage and difficult to supervise mid-process.

Mollick's creative examples include an academic social-science paper from one prompt plus one piece of feedback, a long alliterative rhyming poem, and several playable browser games. He says the game examples were built from vague prompts in Claude Code, with only minor follow-up prompting, and that the art and 3D objects were generated mathematically rather than from external image assets.

Mollick's map example was an isochrone-travel project. He asked Fable to build a researched map showing travel-time regions from cities. He says the model delegated research to other agents, gathered more than 2,200 specific flights, used rail schedules and road-speed sources, and later handled remote-location routes such as Pitcairn Island and Grise Fjord. He describes the result as a sophisticated, working map but not flawless.

Mollick's most ambitious work example was a research-analysis tool for messy survey answers. He first had Fable generate a complex 19-page design document, then execute it. He says the model worked for nine and a half hours and produced Concord, a tool that calibrates human and AI responses across datasets and performs analysis on the results. He says expert review still found errors and omissions, but the scope exceeded prior model outputs he had seen.

Mollick argues that Fable changes the human role from step-by-step operator to commissioner and reviewer. He highlights both the power and the black-box feel of long autonomous runs. He also says Fable's guardrails often fall back to Opus when a task hints at security, limiting legitimate security work.