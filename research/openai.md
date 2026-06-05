---
title: "OpenAI: IPO Outlook & Capital-Web Position"
description: "Provisional profile — $852B valuation, record $122B round, confidential IPO filing, and OpenAI's ~$1.15T compute web."
status: provisional
date: 2026-06-02
tags: [research, provisional, openai, ipo, ai-capital-web]
sources:
  - external-sources/openai-122b-funding-round.md
  - external-sources/openai-nvidia-10gw-partnership.md
  - external-sources/openai-amd-6gw-partnership.md
  - external-sources/openai-oracle-300b-stargate.md
  - external-sources/openai-broadcom-10gw-accelerators.md
  - external-sources/microsoft-openai-pbc-restructuring.md
  - external-sources/openai-coreweave-contracts.md
  - external-sources/openai-infrastructure-1-15-trillion.md
---
> [!CAUTION] Not financial advice — demonstration only
> This is an example / demonstration project. Figures may be provisional, inaccurate, or fictional; nothing here is financial or investment advice. See the [full disclaimer](/README.md).

## Question

Where does OpenAI stand on the path to an IPO, and how is it wired into the AI capital web?

## Context

OpenAI sits at the center of the AI "circular financing" web. As of mid-2026 it is both the most-funded private company in history *and* the largest buyer of AI compute — and it has begun the move to public markets. This doc anchors the [AI capital web](/research/ai-funding-web.md) and pairs with [Anthropic](/research/anthropic.md) and [SpaceX](/research/spacex.md).

> [!NOTE] Snapshot (mid-2026)
> - **Valuation:** ~$852B (post-money, Mar 31 2026 round) — since *overtaken* by Anthropic's $965B
> - **Round:** $122B committed — the largest private round ever
> - **Revenue:** $13.1B booked (2025); ~$25B annualized run-rate (Feb 2026); ~$2B/month
> - **Users:** 900M+ weekly active; 50M+ paying; enterprise >40% of revenue
> - **IPO:** filed *confidentially* with the SEC, targeting H2 2026; $1T listing goal by 2027
> - **Structure:** for-profit recapitalized as **OpenAI Group PBC**, controlled by the nonprofit OpenAI Foundation; Microsoft holds ~27%

## Valuation & funding trajectory

| Date | Event | Valuation |
| --- | --- | ---: |
| Oct 2025 | Recapitalization → OpenAI Group PBC; Microsoft ~~27% (~~$135B) | \~$500B (secondary) |
| Feb 2026 | Round announced ($110B commitments) | $730B (pre-money) |
| Mar 31 2026 | Round closed, $122B committed | **$852B** (post-money) |

The March round drew **up to $50B from Amazon, $30B from Nvidia, and $30B from SoftBank**, co-led by SoftBank with a16z, D. E. Shaw, MGX, TPG, and T. Rowe Price; OpenAI even raised $3B from individuals via bank channels ([OpenAI $122B round](/external-sources/openai-122b-funding-round.md)).

## Revenue & usage

OpenAI booked **$13.1B in 2025** revenue and was generating **\~$2B/month** by the round's close, with an annualized run-rate of \~$20B at end-2025 rising to \~$25B by February 2026 (CFO Sarah Friar; Sacra). It is **not profitable** and, per Sacra, **not cash-flow positive until \~2030** ([source](/external-sources/openai-122b-funding-round.md)).

## Corporate structure

The October 2025 recapitalization turned the for-profit into **OpenAI Group PBC**, controlled by the nonprofit **OpenAI Foundation**. **Microsoft** holds ~~**27%** (~~$135B, down from 32.5% via dilution), committed to buying an incremental **$250B of Azure**, and keeps IP/Azure rights through **2032**, with an independent panel to verify any AGI declaration ([Microsoft–OpenAI](/external-sources/microsoft-openai-pbc-restructuring.md)).

## The compute web: ~$1.15 trillion in commitments

OpenAI has committed an estimated **\~$1.15 trillion** on compute/cloud/chips (2025–2035) — the demand engine of the whole web ([infrastructure breakdown](/external-sources/openai-infrastructure-1-15-trillion.md)):

| Counterparty | Commitment | Nature | Source |
| --- | ---: | --- | --- |
| Broadcom | \~$350B | OpenAI-designed custom accelerators (10 GW) | [↗](/external-sources/openai-broadcom-10gw-accelerators.md) |
| Oracle | \~$300B | Cloud compute (4.5 GW, Stargate) | [↗](/external-sources/openai-oracle-300b-stargate.md) |
| Microsoft | \~$250B | Incremental Azure | [↗](/external-sources/microsoft-openai-pbc-restructuring.md) |
| Nvidia | \~$100B | GPUs/systems (10 GW) **+ up to $100B invested back into OpenAI** | [↗](/external-sources/openai-nvidia-10gw-partnership.md) |
| AMD | \~$90B | Instinct GPUs (6 GW) **+ warrant for \~10% of AMD** | [↗](/external-sources/openai-amd-6gw-partnership.md) |
| Amazon (AWS) | \~$38B | Cloud compute (**+ up to $50B invested into OpenAI**) | [↗](/external-sources/openai-122b-funding-round.md) |
| CoreWeave | \~$22B | GPU cloud (Nvidia \~6% owner + backstops capacity) | [↗](/external-sources/openai-coreweave-contracts.md) |

The striking pattern: **Nvidia and Amazon are simultaneously suppliers *and* equity investors**, and the AMD deal hands OpenAI a \~10% stake in its *supplier*. Money flows in a loop — this is the crux of the "[bubble](/research/ai-funding-web.md)" debate.

## IPO outlook

- **Status:** Confidential SEC filing; targeting **H2 2026**, ahead of a **$1T** listing goal by 2027.
- **Gating factors:** persistent cash burn (no positive cash flow projected until \~2030), the just-completed PBC restructuring (now resolved), and dependence on the durability of its compute commitments.
- **Skeptic view:** NYU's Aswath Damodaran argues the valuation assumes revenue growth no company has sustained at this scale, and that conditional/compute-linked tranches overstate the real cash injection ([source](/external-sources/openai-122b-funding-round.md)).

## Open questions

- How much of the \~$1.15T compute commitment is firm vs. contingent (LOIs, milestone-gated warrants)?
- Does Anthropic's $965B valuation (and faster revenue growth) reset OpenAI's IPO pricing?
- How does the IPO reconcile the nonprofit-controlled PBC structure with public-shareholder expectations?

## Further reading

- [The AI capital web](/research/ai-funding-web.md) — the full funding chart this doc feeds
- [Anthropic](/research/anthropic.md) · [SpaceX](/research/spacex.md)
- Sources: [$122B round](/external-sources/openai-122b-funding-round.md) · [Nvidia](/external-sources/openai-nvidia-10gw-partnership.md) · [AMD](/external-sources/openai-amd-6gw-partnership.md) · [Oracle/Stargate](/external-sources/openai-oracle-300b-stargate.md) · [Broadcom](/external-sources/openai-broadcom-10gw-accelerators.md) · [Microsoft](/external-sources/microsoft-openai-pbc-restructuring.md) · [CoreWeave](/external-sources/openai-coreweave-contracts.md) · [$1.15T infra](/external-sources/openai-infrastructure-1-15-trillion.md)

