---
title: AAPL Live Ticker — a Keyless, Proxy-Free Open Knowledge Embed
description: A genuinely live AAPL stock ticker embedded in the knowledge base
  via an html preview fence — fetched directly from Twelve Data with no proxy
  and no managed key, working because OK's embed CSP allows outbound https and
  Twelve Data sends CORS.
status: provisional
date: 2026-06-09
tags:
  - demo
  - html-preview
  - ticker
  - apple
  - live
---
## A live AAPL ticker, embedded in the KB

A genuinely **live** Apple (AAPL) stock ticker, rendered right inside this document via an [`html preview`](/research/post-ipo-performance.md) fence. It fetches the quote **directly — no proxy, no managed key** — and updates every 60 seconds (or hit **Refresh**).

```html preview h=330px
<div style="font-family:system-ui,sans-serif;padding:18px;color:var(--foreground)">
  <div style="width:min(440px,100%);background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:22px 24px">
    <div style="display:flex;align-items:baseline;justify-content:space-between;gap:12px">
      <div>
        <div id="c-sym" style="font-size:21px;font-weight:700;letter-spacing:.5px">AAPL</div>
        <div id="c-name" style="color:var(--muted-foreground);font-size:13px">Apple Inc.</div>
      </div>
      <div id="c-chg" style="font-size:16px;font-weight:600;font-variant-numeric:tabular-nums;color:var(--muted-foreground)">—</div>
    </div>
    <div id="c-price" style="margin:13px 0 6px;font-size:46px;font-weight:700;font-variant-numeric:tabular-nums;color:var(--muted-foreground);transition:color .2s">—</div>
    <div style="margin-top:18px;display:grid;grid-template-columns:1fr 1fr;gap:10px 16px;border-top:1px solid var(--border);padding-top:15px">
      <div><div style="color:var(--muted-foreground);font-size:11px;text-transform:uppercase;letter-spacing:.4px">Prev close</div><div id="c-prev" style="font-size:15px;font-variant-numeric:tabular-nums;margin-top:2px">—</div></div>
      <div><div style="color:var(--muted-foreground);font-size:11px;text-transform:uppercase;letter-spacing:.4px">Open</div><div id="c-open" style="font-size:15px;font-variant-numeric:tabular-nums;margin-top:2px">—</div></div>
      <div><div style="color:var(--muted-foreground);font-size:11px;text-transform:uppercase;letter-spacing:.4px">Day range</div><div id="c-day" style="font-size:15px;font-variant-numeric:tabular-nums;margin-top:2px">—</div></div>
      <div><div style="color:var(--muted-foreground);font-size:11px;text-transform:uppercase;letter-spacing:.4px">52w range</div><div id="c-52" style="font-size:15px;font-variant-numeric:tabular-nums;margin-top:2px">—</div></div>
    </div>
    <div style="margin-top:16px;display:flex;align-items:center;justify-content:space-between;gap:8px;color:var(--muted-foreground);font-size:12px">
      <span style="display:flex;align-items:center;gap:6px"><span id="c-dot" style="width:8px;height:8px;border-radius:50%;background:var(--muted-foreground);display:inline-block"></span><span id="c-status">Loading…</span></span>
      <button id="c-refresh" style="padding:3px 10px;border:1px solid var(--border);border-radius:var(--radius);background:var(--card);color:var(--foreground);cursor:pointer;font-size:12px;font-weight:600">↻ Refresh</button>
    </div>
    <div id="c-diag" style="margin-top:9px;font-size:11px;font-family:ui-monospace,Menlo,monospace;color:var(--muted-foreground);word-break:break-all"></div>
  </div>
  <script>
  (function(){
    var SYM='AAPL';
    var url='https://api.twelvedata.com/quote?symbol='+SYM+'&apikey=demo'; // public demo token, DIRECT — no proxy
    function $(id){return document.getElementById(id);}
    function n(v){return (v==null||isNaN(+v))?'—':(+v).toLocaleString('en-US',{minimumFractionDigits:2,maximumFractionDigits:2});}
    $('c-diag').textContent='Source: api.twelvedata.com';
    function tick(){
      $('c-status').textContent='Fetching…';
      fetch(url).then(function(r){return r.json();}).then(function(d){
        if(d.code){throw new Error(d.message||('code '+d.code));}
        var price=+d.close, prev=+d.previous_close, ch=+d.change, pct=+d.percent_change, up=ch>=0;
        var col=up?'var(--chart-2)':'var(--destructive)', sg=up?'+':'−';
        $('c-sym').textContent=d.symbol||SYM; $('c-name').textContent=(d.name||'')+(d.exchange?' · '+d.exchange:'');
        var pe=$('c-price'); pe.textContent='$'+n(price); pe.style.color=col;
        var ce=$('c-chg'); ce.textContent=sg+n(Math.abs(ch))+' ('+sg+n(Math.abs(pct))+'%)'; ce.style.color=col;
        $('c-prev').textContent='$'+n(prev); $('c-open').textContent='$'+n(d.open);
        $('c-day').textContent=n(d.low)+' – '+n(d.high);
        var w=d.fifty_two_week||{}; $('c-52').textContent=n(w.low)+' – '+n(w.high);
        $('c-dot').style.background='var(--chart-2)'; $('c-status').textContent='Live'+(d.is_market_open?' · market open':' · last close');
      }).catch(function(e){
        $('c-dot').style.background='var(--destructive)';
        $('c-status').textContent='Blocked: '+(e&&e.message?e.message:String(e));
      });
    }
    $('c-refresh').addEventListener('click',tick);
    tick(); setInterval(tick,60000);
  })();
  </script>
</div>
```

## Related

- [Post-IPO Returns: IPO Day → 5 Years](/research/post-ipo-performance.md) — a companion `html preview` demo that ships its data inline (no fetch).
- [Historical Tech IPOs by Year](/research/historical-tech-ipos.md) — another inline-data chart embed.
