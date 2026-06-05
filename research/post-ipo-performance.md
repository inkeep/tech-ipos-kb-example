---
title: "Post-IPO Returns: Our Picks vs the Average IPO, IPO Day → 5 Years"
description: An animated line-race of the return from buying Uber, Snowflake,
  Rivian and Tesla at their IPO offer price, benchmarked against the average and
  median U.S. IPO (Ritter data) — from IPO day out to five years. A
  demonstration of Open Knowledge's live html-preview embeds.
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
  - external-sources/ritter-ipo-long-run-returns.md
  - external-sources/market-caps-may-2026.md
---
## Question

If you'd bought a tech IPO **at the offer price**, what return would you be sitting on, month by month, from IPO day out to five years — and how do our hand-picked names compare to a *typical* IPO? This page animates the **return since IPO** for [Uber](https://companiesmarketcap.com/uber/), [Snowflake](https://companiesmarketcap.com/snowflake/), [Rivian](https://companiesmarketcap.com/rivian/), and [Tesla](https://companiesmarketcap.com/tesla/) (the generational benchmark), against two dashed reference lines: the **average (mean)** and **typical (median)** U.S. IPO from [Jay Ritter's data](/external-sources/ritter-ipo-long-run-returns.md). 0% = breakeven.

It doubles as a demonstration of Open Knowledge's live, themed [`html preview`](/external-sources/post-ipo-stock-performance-figures.md) embeds — the chart re-skins to your theme, replays on demand, and toggles log/linear scale.

## The race: your return since IPO (bought at the offer price)

```html preview h=500px
<div style="font-family:system-ui,sans-serif;padding:14px 16px;color:var(--foreground)">
  <h3 style="margin:0 0 3px;font-size:15px;font-weight:650">Return since IPO — our picks vs the average IPO</h3>
  <p style="margin:0 0 10px;font-size:11.5px;line-height:1.45;color:var(--muted-foreground)">Cumulative % return buying at the IPO offer price, animated from IPO day to year 5. 0% = breakeven. Solid = individual stocks; <b>dashed = all-U.S.-IPO benchmarks</b> (mean &amp; median, Ritter 1980–2024). Use <b>Log</b> to keep Tesla readable. Points are documented anchors, interpolated between.</p>
  <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap;margin-bottom:8px">
    <button id="pp-replay" style="padding:4px 11px;border:1px solid var(--border);border-radius:var(--radius);background:var(--card);color:var(--foreground);cursor:pointer;font-size:12px;font-weight:600">▶ Replay</button>
    <button id="pp-scale" style="padding:4px 11px;border:1px solid var(--border);border-radius:var(--radius);background:var(--card);color:var(--foreground);cursor:pointer;font-size:12px;font-weight:600">Scale: Log</button>
    <div id="pp-clock" style="font-size:12.5px;font-weight:650;font-variant-numeric:tabular-nums">Month 0 · IPO day</div>
    <div id="pp-legend" style="display:flex;gap:12px;margin-left:auto;font-size:11px;font-variant-numeric:tabular-nums;flex-wrap:wrap;justify-content:flex-end"></div>
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
      {name:'Tesla',t:'TSLA',c:'var(--chart-5)',a:[[0,100],[0.2,140],[6,157],[18,168],[30,203],[42,885],[54,1308],[60,1560]]},
      {name:'Average IPO (mean)',t:'AVG',c:'var(--chart-3)',dash:'7 5',a:[[0,100],[0.2,118.9],[12,125.6],[36,136.3],[60,157.2]]},
      {name:'Typical IPO (median)',t:'MED',c:'var(--muted-foreground)',dash:'2 5',a:[[0,100],[36,83.4],[60,77.9]]}
    ];
    var W=600,H=400,L=56,R=86,T=22,B=42,PW=W-L-R,PH=H-T-B,XM=60;
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
      var la={fill:'none',stroke:co.c,'stroke-width':co.dash?2:2.6,'stroke-linejoin':'round','stroke-linecap':'round'};
      if(co.dash)la['stroke-dasharray']=co.dash;
      co.line=svg('polyline',la);S.appendChild(co.line);
      co.dot=svg('circle',{r:co.dash?3:4,fill:co.c,stroke:'var(--background)','stroke-width':1.5});S.appendChild(co.dot);
      co.lab=svg('text',{'font-size':10,'font-weight':700,fill:co.c});S.appendChild(co.lab);
      co.maxM=co.a[co.a.length-1][0];
      co.chip=document.createElement('span');co.chip.innerHTML='<span style="display:inline-block;width:'+(co.dash?'14px':'9px')+';height:'+(co.dash?'0':'9px')+';'+(co.dash?'border-top:2px '+(co.dash[0]==='2'?'dotted':'dashed')+' '+co.c+';':'border-radius:2px;background:'+co.c+';')+'margin-right:4px;vertical-align:middle"></span><b>'+co.t+'</b> <span class="v"></span>';leg.appendChild(co.chip);
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
> - **Solid lines** are individual stocks; **dashed lines** are the all-U.S.-IPO benchmarks (mean & median, ~9,250 IPOs, 1980–2024).
> - **The mean (AVG) and median (MED) tell opposite stories.** The *average* IPO is up ~+57% from the offer by year 5 — but the *median* IPO is **down ~22%**. The mean is dragged up by a thin tail of moonshots (Tesla is literally one of them); the typical IPO loses money.
> - **Our four picks bracket the benchmarks:** Snowflake (+79%) and a recovered Uber (+47%) beat the median handily; Rivian (−80%) is deep in the losing tail; Tesla is the moonshot that *makes* the mean.

## How do our four compare to the average IPO?

The answer to "what about everything outside our set" is the two dashed lines — and the gap between them is the whole point. Buying at the offer price and holding, here's the all-market picture from [Ritter's data](/external-sources/ritter-ipo-long-run-returns.md):

| From the IPO **offer price** | 3 years | 5 years |
| --- | ---: | ---: |
| **Average (mean) IPO** | +36% | +57% |
| **Typical (median) IPO** | −17% | −22% |
| Share of IPOs that *lose money* (3-yr) | — | **~56%** |
| Avg IPO vs size-matched market | underperforms by **~3.3%/yr** over years 1–5 | |

So our four aren't a representative sample — **no four ever could be.** More than half of all IPOs are underwater three years on; the average looks fine only because a few giant winners (Tesla, Yahoo!, Moderna, Nvidia…) pull the mean far above the median. That's the real lesson for the [2026 cohort](/research/historical-tech-ipos.md): the headline is set by the moonshots, but the base rate is a coin-flip-to-losing bet.

## What this says about the 2026 class

The [2026 cohort](/research/historical-tech-ipos.md) — [SpaceX](/research/spacex.md), [OpenAI](/research/openai.md), [Anthropic](/research/anthropic.md) — debuts at valuations an order of magnitude larger than anything here. The IPO-day headline (capital raised) is what the [by-year chart](/research/historical-tech-ipos.md) measures; *this* page measures the return an IPO buyer actually earns afterward — and the base rates above are the prior any 2026 buyer is betting against.

## Method & caveats

- **"Bought at the IPO"** = bought at the **offer price**. Return % = (price ÷ offer price − 1) × 100. Individual-stock anchors are the IPO offer, first-day close, post-IPO peak, and calendar year-end closes ([reference](/external-sources/post-ipo-stock-performance-figures.md)); the line interpolates between them — not a literal monthly series.
- **Benchmark lines** are equal-weighted, all-U.S.-IPO buy-and-hold returns from the offer price, anchored at the average first-day return (+18.9%), the 1-year average return, and the 3- and 5-year mean/median BHR from [Ritter (1980–2024)](/external-sources/ritter-ipo-long-run-returns.md), interpolated between. They exclude offer prices under $5, SPACs, ADRs, REITs, and closed-end funds.
- **Tesla is a 2010 IPO**, included only as a scale benchmark — nominal (pre-split) closes; returns are split-invariant. **Log vs linear** changes only the y-axis. **5-year reach:** Rivian (Nov 2021) is ~4.5 years public, so its line stops near month 55. Price return only.

Sources: [post-IPO price reference](/external-sources/post-ipo-stock-performance-figures.md) · [Ritter IPO long-run returns](/external-sources/ritter-ipo-long-run-returns.md) · [market caps May 2026](/external-sources/market-caps-may-2026.md).

## Further reading

- [Historical Tech IPOs by Year — and Where 2026 Fits](/research/historical-tech-ipos.md) — the capital-raised companion chart
- The 2026 cohort: [SpaceX](/research/spacex.md) · [OpenAI](/research/openai.md) · [Anthropic](/research/anthropic.md)
