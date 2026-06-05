---
title: "Post-IPO Returns: Recent Cohort + Tesla, IPO Day → 5 Years"
description: An animated line-race of the return you'd have earned buying Uber,
  Snowflake, Rivian — and Tesla, the generational benchmark — at their IPO offer
  price, from IPO day out to five years. A demonstration of Open Knowledge's
  live html-preview embeds.
status: provisional
date: 2026-06-05
tags:
  - research
  - provisional
  - ipo
  - stock-performance
  - returns
  - chart
  - animated
sources:
  - external-sources/post-ipo-stock-performance-figures.md
  - external-sources/market-caps-may-2026.md
---
## Question

If you'd bought a tech IPO **at the offer price**, what return would you be sitting on, month by month, from IPO day out to five years? This page animates the **return since IPO** for the 2019–2021 cohort — [Uber](https://companiesmarketcap.com/uber/), [Snowflake](https://companiesmarketcap.com/snowflake/), [Rivian](https://companiesmarketcap.com/rivian/) — plus [Tesla](https://companiesmarketcap.com/tesla/) (2010), included as the *generational winner* for scale. 0% = breakeven (you paid the offer price), positive = profit, negative = underwater.

It doubles as a demonstration of Open Knowledge's live, themed [`html preview`](/external-sources/post-ipo-stock-performance-figures.md) embeds — the chart is a self-contained animation that re-skins to your theme, replays on demand, and toggles between log and linear scale.

## The race: your return since IPO (bought at the offer price)

```html preview h=486px
<div style="font-family:system-ui,sans-serif;padding:14px 16px;color:var(--foreground)">
  <h3 style="margin:0 0 3px;font-size:15px;font-weight:650">Return since IPO — if you bought at the offer price</h3>
  <p style="margin:0 0 10px;font-size:11.5px;line-height:1.45;color:var(--muted-foreground)">Cumulative % return buying at the IPO offer price, animated from IPO day to year 5. 0% = breakeven. <b>Tesla (2010)</b> is a different era, shown for scale — use <b>Log</b> to keep all four readable, <b>Linear</b> to see how far Tesla outruns the rest. Points are documented anchors (offer, day-1 close, peak, year-end closes), interpolated between.</p>
  <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap;margin-bottom:8px">
    <button id="pp-replay" style="padding:4px 11px;border:1px solid var(--border);border-radius:var(--radius);background:var(--card);color:var(--foreground);cursor:pointer;font-size:12px;font-weight:600">▶ Replay</button>
    <button id="pp-scale" style="padding:4px 11px;border:1px solid var(--border);border-radius:var(--radius);background:var(--card);color:var(--foreground);cursor:pointer;font-size:12px;font-weight:600">Scale: Log</button>
    <div id="pp-clock" style="font-size:12.5px;font-weight:650;font-variant-numeric:tabular-nums">Month 0 · IPO day</div>
    <div id="pp-legend" style="display:flex;gap:13px;margin-left:auto;font-size:11.5px;font-variant-numeric:tabular-nums;flex-wrap:wrap"></div>
  </div>
  <svg id="pp-chart" viewBox="0 0 600 400" style="width:100%;height:auto;display:block" aria-label="Animated post-IPO return line chart"></svg>
  <script>
  (function(){
    var S=document.getElementById('pp-chart');
    // anchors: price indexed to offer=100; return % = value - 100
    var COS=[
      {name:'Uber',t:'UBER',c:'var(--chart-1)',a:[[0,100],[0.3,92],[7,66],[19,113],[31,93],[43,55],[55,137],[60,147]]},
      {name:'Snowflake',t:'SNOW',c:'var(--chart-2)',a:[[0,100],[0.2,212],[3.5,234],[14,335],[15.5,282],[27,119],[39,165],[51,128],[60,179]]},
      {name:'Rivian',t:'RIVN',c:'var(--chart-4)',a:[[0,100],[0.2,129],[0.6,220],[2,133],[14,24],[26,30],[38,17],[48,24],[55,20]]},
      {name:'Tesla',t:'TSLA',c:'var(--chart-5)',a:[[0,100],[0.2,140],[6,157],[18,168],[30,203],[42,885],[54,1308],[60,1560]]}
    ];
    var W=600,H=400,L=56,R=80,T=22,B=42,PW=W-L-R,PH=H-T-B,XM=60;
    var scale='log';
    var LMIN=-100,LMAX=1500;
    var GLO=12,GHI=2000,llo=Math.log(GLO)/Math.LN10,lhi=Math.log(GHI)/Math.LN10;
    function x(m){return L+(m/XM)*PW;}
    function yLin(v){return T+(1-((v-100)-LMIN)/(LMAX-LMIN))*PH;}
    function yLog(v){var c=v<1?1:v;return T+(1-((Math.log(c)/Math.LN10)-llo)/(lhi-llo))*PH;}
    function y(v){return scale==='log'?yLog(v):yLin(v);}
    function val(a,m){if(m<=a[0][0])return a[0][1];for(var i=1;i<a.length;i++){if(m<=a[i][0]){var p=a[i-1],q=a[i],f=(m-p[0])/(q[0]-p[0]);return p[1]+(q[1]-p[1])*f;}}return a[a.length-1][1];}
    function fmt(r){return(r>0?'+':'')+Math.round(r)+'%';}
    function svg(tag,at){var e=document.createElementNS('http://www.w3.org/2000/svg',tag);for(var k in at)e.setAttribute(k,at[k]);return e;}
    // x gridlines + axis (built once)
    var xs=svg('g',{});
    [0,12,24,36,48,60].forEach(function(m){
      xs.appendChild(svg('line',{x1:x(m),y1:T,x2:x(m),y2:T+PH,stroke:'var(--border)','stroke-opacity':0.35,'stroke-width':1}));
      var tx=svg('text',{x:x(m),y:T+PH+15,'text-anchor':'middle','font-size':10,fill:'var(--muted-foreground)'});tx.textContent=m===0?'IPO':(m/12)+'yr';xs.appendChild(tx);
    });
    var ax=svg('text',{x:L+PW/2,y:H-4,'text-anchor':'middle','font-size':10,fill:'var(--muted-foreground)'});ax.textContent='Years since IPO';xs.appendChild(ax);
    S.appendChild(xs);
    // y gridlines (rebuilt on scale change)
    var gridG=svg('g',{});S.appendChild(gridG);
    function buildGrid(){
      while(gridG.firstChild)gridG.removeChild(gridG.firstChild);
      var rows=scale==='log'
        ? [[25,'-75%'],[50,'-50%'],[100,'0%'],[200,'+100%'],[500,'+400%'],[1000,'+900%'],[2000,'+1900%']]
        : [[100,'0%'],[350,'+250%'],[600,'+500%'],[850,'+750%'],[1100,'+1000%'],[1350,'+1250%'],[1600,'+1500%']];
      rows.forEach(function(row){
        var v=row[0],base=v===100;
        gridG.appendChild(svg('line',{x1:L,y1:y(v),x2:L+PW,y2:y(v),stroke:base?'var(--foreground)':'var(--border)','stroke-opacity':base?0.5:0.5,'stroke-width':base?1.3:1,'stroke-dasharray':base?'5 4':'2 4'}));
        var tx=svg('text',{x:L-7,y:y(v)+3.5,'text-anchor':'end','font-size':9.5,fill:'var(--muted-foreground)'});tx.textContent=row[1];gridG.appendChild(tx);
      });
      var bl=svg('text',{x:L+PW,y:y(100)-5,'text-anchor':'end','font-size':9.5,fill:'var(--muted-foreground)','font-style':'italic'});bl.textContent='0% = bought at IPO offer (breakeven)';gridG.appendChild(bl);
    }
    // dynamic layer
    var leg=document.getElementById('pp-legend');
    COS.forEach(function(co){
      co.line=svg('polyline',{fill:'none',stroke:co.c,'stroke-width':2.6,'stroke-linejoin':'round','stroke-linecap':'round'});S.appendChild(co.line);
      co.dot=svg('circle',{r:4,fill:co.c,stroke:'var(--background)','stroke-width':1.5});S.appendChild(co.dot);
      co.lab=svg('text',{'font-size':10.5,'font-weight':700,fill:co.c});S.appendChild(co.lab);
      co.maxM=co.a[co.a.length-1][0];
      co.chip=document.createElement('span');co.chip.innerHTML='<span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:'+co.c+';margin-right:4px;vertical-align:middle"></span><b>'+co.t+'</b> <span class="v"></span>';leg.appendChild(co.chip);
    });
    var clock=document.getElementById('pp-clock');
    function draw(cm){
      clock.textContent='Month '+Math.floor(cm)+(cm<0.5?' · IPO day':' · ~'+(cm/12).toFixed(1)+' yrs');
      COS.forEach(function(co){
        var end=Math.min(cm,co.maxM),pts=[],m;
        for(m=0;m<end;m+=0.4)pts.push(x(m)+','+y(val(co.a,m)));
        pts.push(x(end)+','+y(val(co.a,end)));
        co.line.setAttribute('points',pts.join(' '));
        var vv=val(co.a,end),rr=vv-100,done=cm>=co.maxM;
        co.dot.setAttribute('cx',x(end));co.dot.setAttribute('cy',y(vv));co.dot.setAttribute('opacity',cm<0.05?0:1);
        co.lab.setAttribute('x',Math.min(x(end)+7,W-2));co.lab.setAttribute('y',y(vv)+3.5);
        co.lab.textContent=(done?co.t+' ':'')+fmt(rr);
        co.chip.querySelector('.v').textContent=fmt(rr);
      });
    }
    var DUR=7200,st=null,raf=null,cur=0;
    function fr(ts){if(st===null)st=ts;var p=Math.min((ts-st)/DUR,1);cur=p*XM;draw(cur);if(p<1)raf=requestAnimationFrame(fr);else{cur=XM;draw(XM);}}
    function play(){if(raf)cancelAnimationFrame(raf);st=null;raf=requestAnimationFrame(fr);}
    document.getElementById('pp-replay').addEventListener('click',play);
    document.getElementById('pp-scale').addEventListener('click',function(){scale=scale==='log'?'linear':'log';this.textContent='Scale: '+(scale==='log'?'Log':'Linear');buildGrid();draw(cur);});
    buildGrid();draw(0);play();
  })();
  </script>
</div>
```

> [!NOTE] How to read it
> - **Above 0%** = in profit on your IPO buy; **below 0%** = underwater. Every line starts at 0% on IPO day because you bought *at* the offer price.
> - **Tesla (2010)** is the benchmark — **~+1,460% by year 5**, on a completely different scale from the recent cohort. On **Log** it's a steep climber among readable peers; flip to **Linear** and it rockets off the top while the other three flatten near 0% — which is the point.
> - **Snowflake** jumps to **+112% on day one** (offer $120, opened ~$245), peaks +235% (late 2021), then round-trips most of it.
> - **Uber** is underwater ~4.5 years (bottom ~−45% in 2022) before its +143% 2023 pushes it green.
> - **Rivian** is the cautionary tale: briefly +120%, then −82% in 2022, still ~−80% at year 4.

## What the cohort says about the 2026 class

The lines diverge so hard there's no single "average" IPO return — buying at the IPO, your four-year outcome ranged from **+1,200%** (Tesla) to **−80%** (Rivian). Tesla is the dream the others are measured against; for the recent cohort, the realistic spread was roughly **−80% to +40%**, and even the best of them (Snowflake) gave back a +235% gain.

That's the backdrop for the [2026 cohort](/research/historical-tech-ipos.md) — [SpaceX](/research/spacex.md), [OpenAI](/research/openai.md), [Anthropic](/research/anthropic.md) — debuting at valuations an order of magnitude larger. The IPO-day headline (capital raised) is what the [by-year chart](/research/historical-tech-ipos.md) measures; *this* page measures the return an IPO buyer actually earns over the following five years.

## Method & caveats

- **"Bought at the IPO"** = bought at the **offer price** ($17 Tesla / $45 Uber / $120 Snowflake / $78 Rivian). Return % = (price ÷ offer price − 1) × 100 — the price IPO-allocation investors pay. (A buyer at the *first-day close* would have a lower-starting curve.)
- **Tesla is a 2010 IPO**, included only as a scale benchmark — not part of the 2019–2021 cohort. Its figures are nominal (pre-split) closes; Tesla later split 15:1, but **returns are split-invariant**, so the IPO-buyer return is unaffected ([detail + reconciliation](/external-sources/post-ipo-stock-performance-figures.md)).
- **Log vs linear:** the toggle changes only the y-axis. Log keeps a 1,500%-range winner and a −80% loser on one readable chart; linear shows the true magnitude gap.
- **Anchors, not ticks:** plotted points are the IPO offer, first-day close, post-IPO peak, and each **calendar year-end close**; the line interpolates between them — not a literal monthly series. Every figure + source is in the [compiled reference](/external-sources/post-ipo-stock-performance-figures.md).
- **5-year reach:** Tesla, Uber, and Snowflake have a full 5 years; **Rivian** (Nov 2021) is only ~4.5 years public as of June 2026, so its line stops near month 55. Price return only (none pay a dividend).

Source for all figures: [post-IPO stock performance reference](/external-sources/post-ipo-stock-performance-figures.md) · prior-art valuations: [market caps May 2026](/external-sources/market-caps-may-2026.md).

## Further reading

- [Historical Tech IPOs by Year — and Where 2026 Fits](/research/historical-tech-ipos.md) — the capital-raised companion chart
- The 2026 cohort: [SpaceX](/research/spacex.md) · [OpenAI](/research/openai.md) · [Anthropic](/research/anthropic.md)
