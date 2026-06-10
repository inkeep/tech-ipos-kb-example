---
title: Business Insider Tests Claude Fable 5 Safeguards
description: Business Insider report on Claude Fable 5 fallbacks and false positives for cybersecurity, biology, chemistry, and distillation requests.
source_url: https://www.businessinsider.com/anthropic-claude-fable-5-safeguards-block-requests-cybersecurity-biology-2026-6
media_type: text/html
date_fetched: 2026-06-10
author: Kelsey Vlamis, Business Insider
preservation: text-extracted
tags:
  - source
  - immutable
  - layer-ingest
  - text
  - anthropic
  - fable
  - safeguards
  - claude
---
## Extracted source notes

Business Insider reported on June 10, 2026 that Claude Fable 5's public release includes broad safeguards that can block or reroute some benign cybersecurity and biology prompts. The article says Business Insider tested simple cancer-related questions and saw Claude switch from Fable 5 to Opus 4.8 before answering.

The article reports that Anthropic described three categories likely to trigger Fable 5 safeguards: cybersecurity, biology and chemistry, and distillation of Fable 5's capabilities. When triggered, Fable 5 may either refuse or route the response to Opus 4.8, depending on user preference.

Business Insider quotes Anthropic's position that the model's scientific capabilities made conservative safeguards necessary for broad release. The company said early data showed more than 95% of Fable sessions did not fall back to Opus, but also acknowledged that normal safe content may be caught and that it plans to reduce false positives.

The article says Anthropic plans to make Mythos-class capabilities available to broader biology and life-sciences communities through a trusted-access path, while preserving additional controls for public access.

The report frames the safeguards as a tradeoff: they reduce risk from misuse, but may obscure how powerful the model is and can frustrate benign users who are working near sensitive domains.