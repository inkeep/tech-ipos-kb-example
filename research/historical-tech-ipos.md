---
title: "Historical Tech IPOs by Year — and Where 2026 Fits"
description: "A chart of the largest technology IPO each year by capital raised (1995–2026), showing how SpaceX/OpenAI/Anthropic compare to past records."
status: provisional
date: 2026-06-02
tags: [research, provisional, ipo, history, chart]
sources:
  - external-sources/historical-tech-ipo-figures.md
  - external-sources/cnbc-biggest-tech-ipos-2020.md
  - external-sources/spacex-ipo-s1-filing.md
  - external-sources/openai-122b-funding-round.md
  - external-sources/anthropic-series-h-65b.md
---
> [!CAUTION] Not financial advice — demonstration only
> This is an example / demonstration project. Figures may be provisional, inaccurate, or fictional; nothing here is financial or investment advice. See the [full disclaimer](/README.md).

## Question

How big are the impending 2026 tech IPOs ([SpaceX](/research/spacex.md), [OpenAI](/research/openai.md), [Anthropic](/research/anthropic.md)) compared to the largest tech IPOs of past years?

## Context

Tech IPOs have escalated in waves — from Netscape's $140M debut that opened the dot-com era, to the $16–22B Facebook/Alibaba peak of the 2010s, to a potential **\~$75B SpaceX raise** that would dwarf every IPO in any sector. This doc charts the marquee tech IPO of each milestone year and sets the 2026 cohort against it. All figures cite the [compiled reference](/external-sources/historical-tech-ipo-figures.md) and [CNBC](/external-sources/cnbc-biggest-tech-ipos-2020.md).

## Chart: largest tech IPO by year (capital raised)

```html preview h=362px w=561px
<div style="font-family:system-ui,sans-serif;padding:18px;color:var(--foreground)">
  <h3 style="margin:0 0 2px;font-size:15px;font-weight:600">Largest tech IPO by year — capital raised ($B)</h3>
  <p style="margin:0 0 16px;font-size:12px;color:var(--muted-foreground)">SpaceX's ~$75B target (dashed) would be ~3.4× the prior tech record, Alibaba 2014 (amber). Bars are linear — early IPOs are tiny by design; labels show each raise.</p>
  <div id="ipobars" style="display:flex;align-items:flex-end;gap:10px;height:250px"></div>
  <script>
    var data = [
      {n:'Netscape', y:1995, v:0.14, c:'var(--chart-1)'},
      {n:'Google', y:2004, v:1.67, c:'var(--chart-1)'},
      {n:'Facebook', y:2012, v:16.0, c:'var(--chart-1)'},
      {n:'Alibaba', y:2014, v:21.8, c:'var(--chart-3)'},
      {n:'Uber', y:2019, v:8.1, c:'var(--chart-1)'},
      {n:'Snowflake', y:2020, v:3.4, c:'var(--chart-1)'},
      {n:'Rivian', y:2021, v:11.9, c:'var(--chart-1)'},
      {n:'SpaceX', y:2026, v:75, c:'var(--chart-5)', t:1}
    ];
    var max = Math.max.apply(null, data.map(function(d){ return d.v; }));
    document.getElementById('ipobars').innerHTML = data.map(function(d){
      var h = Math.max(d.v / max * 100, 0.8);
      var bar = d.t
        ? 'border:2px dashed var(--chart-5);background:transparent;'
        : 'background:' + d.c + ';';
      return '<div style="flex:1;display:flex;flex-direction:column;align-items:center;gap:5px;height:100%;justify-content:flex-end">'
        + '<span style="font-size:11.5px;font-weight:700">$' + d.v + 'B</span>'
        + '<div title="' + d.n + ' ' + d.y + ': $' + d.v + 'B" style="width:100%;height:' + h + '%;min-height:2px;' + bar + 'border-radius:var(--radius) var(--radius) 0 0"></div>'
        + '<span style="font-size:11.5px;font-weight:600">' + d.n + '</span>'
        + '<span style="font-size:10.5px;color:var(--muted-foreground)">' + d.y + '</span>'
        + '</div>';
    }).join('');
  </script>
</div>
```

> [!NOTE] Where the 2026 cohort fits
> - **SpaceX (~$75B target)** would be the **largest IPO in history** — ~3.4× Alibaba (the prior tech record) and ~3× Saudi Aramco (the prior all-sector record). Now priced at a **fixed $135/share** (~555.6M shares ≈ $75B) ahead of the ~June 11 pricing ([$135 pricing](/external-sources/spacex-ipo-135-price.md)).
> - **OpenAI** has filed *confidentially* and **Anthropic** is expected to follow — neither has a set raise yet, so they don't appear as bars. For scale, their *private valuations* ($852B / $965B) already rival the IPO-day market caps of the biggest historical debuts ([OpenAI](/external-sources/openai-122b-funding-round.md), [Anthropic](/external-sources/anthropic-series-h-65b.md)).

## Dataset (by year)

| Year | Company | Raised | IPO valuation | Exchange | Note |
| --- | --- | ---: | ---: | --- | --- |
| 1995 | Netscape | \~$0.14B | \~$3B | NASDAQ | Opened the dot-com era |
| 2004 | Google | $1.67B | \~$23B | NASDAQ | Dutch-auction IPO |
| 2008 | Visa | $17.9B | — | NYSE | Fintech; U.S. record at the time |
| 2012 | Facebook | $16.0B | \~$104B | NASDAQ | Largest U.S. tech IPO until 2014 |
| 2014 | Alibaba | $21.8B | \~$231B | NYSE | **Largest tech IPO ever** |
| 2019 | Uber | $8.1B | \~$82B | NYSE | Largest ride-hailing IPO |
| 2020 | Snowflake | $3.4B | $33.2B | NYSE | Largest software IPO (Airbnb $3.5B, DoorDash $3.4B same year) |
| 2021 | Rivian | $11.9B | \~$66.5B | NASDAQ | Largest EV IPO |
| 2026 | **SpaceX** | up to \~$75B | \~$1.75T | NASDAQ (SPCX) | **Would be the largest IPO ever** |

Source: [historical tech IPO figures](/external-sources/historical-tech-ipo-figures.md) · [CNBC tech-IPO ranking](/external-sources/cnbc-biggest-tech-ipos-2020.md).

## All-time records, for scale (all sectors)

Saudi Aramco **$25.6B** (2019) · Alibaba **$21.8B** (2014) · SoftBank **$21.3B** (2018) · NTT DoCoMo **$18.1B** (1998) · Visa **$17.9B** (2008) · Facebook **$16.0B** (2012). SpaceX's target would top them all ([source](/external-sources/historical-tech-ipo-figures.md)).

## Caveats

- **"Tech" is fuzzy** — Visa (fintech) and Alibaba (Chinese e-commerce on a U.S. exchange) are sometimes excluded from "U.S. tech" rankings (see [CNBC](/external-sources/cnbc-biggest-tech-ipos-2020.md)).
- **Direct listings excluded** — Coinbase, Spotify, Roblox, Palantir, Slack raised no IPO capital, so they're absent from a "capital raised" chart despite large debuts.
- **SpaceX's raise**: earlier trackers cited \~$30B; S-1 reporting cited up to \~$75B; it is now set at a **fixed $135/share × \~555.6M shares ≈ $75B** ([$135 pricing](/external-sources/spacex-ipo-135-price.md)) — reported but unofficial until the pricing notice.

## Further reading

- The 2026 cohort: [SpaceX](/research/spacex.md) · [OpenAI](/research/openai.md) · [Anthropic](/research/anthropic.md)
- [Post-IPO Returns: IPO Day → 5 Years](/research/post-ipo-performance.md) — the animated companion: your **% return** buying at the IPO over the five years after listing (Uber, Snowflake, Rivian)
- [The AI capital web](/research/ai-funding-web.md) — the funding chart for the AI side of this cohort

