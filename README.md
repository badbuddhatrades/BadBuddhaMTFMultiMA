# BadBuddhaMTFMultiMABadBuddha MTF Multi‑MA (MTF MMA)

Multi‑timeframe moving averages with clean visuals, lightweight rendering, and sensible defaults for intraday futures. Built for NinjaTrader® 8.


**Highlights**

True Multi‑TF: Pull MAs from any supported timeframe (1m → 60m) while you stay on your preferred chart.

* Four MA Lanes: 9 • 20 • 50 • 200 by default (all toggleable). Each lane can choose SMA/EMA/WMA.
* Clouds: Optional shading between two lanes (e.g., 9↔20 or 20↔50) for instant trend bias. **Coming Soon**
* Flip Cues (optional): Lightweight markers when price closes across a selected MA on the higher‑TF feed. **Coming Soon**
* Lean Rendering: Efficient drawing paths and throttled updates to keep your chart snappy.
* Style First: Thoughtful color defaults (green 9, red 20, light‑blue 50, gray 200) that don’t fight your candles.

This is an indicator, not a strategy. It doesn’t submit, modify, or manage orders.

**What it’s for**

When you scalp on a 3–5 minute chart but you care about the 10m/15m trend, switching charts or overlaying multiple panels can get messy. MTF MMA pipes those higher‑timeframe MAs directly onto your working chart, so you get the story at a glance:

* Are we above 9/20 on the 10m? Is the 20 over the 50?
* Did price just flip through the 9 on the 10m while I’m watching a 3m pullback?
* Is the fast/slow cloud expanding or contracting?  **Coming Soon**
* Stay focused on execution while keeping context in view.

**Requirements**

* NinjaTrader 8.1+ (tested on recent 8.1 builds)
* A standard chart with enough bars to load the chosen higher timeframe

**Install**

* Download the .zip from your purchase/download page (do not unzip).
* NinjaTrader → Control Center → Tools → Import → NinjaScript Add‑On…
* Select the zip. Restart NinjaTrader after import if prompted.
* If Windows blocked the zip, right‑click it → Properties → check Unblock → Apply. Then import.

**Quick start (recommended defaults)**
* Chart: 10‑minute or 5‑minute for indices/GC/CL
* Lanes: 9 (EMA), 20 (EMA), 50 (EMA), 200 (SMA)
* MTF Source: Same as chart to start; then try pulling 10m MAs while working on a 3m chart
* Cloud: On (9↔20)

**Parameters (overview)**

* Timeframe Source: Chart (use the current chart’s TF) or pick a higher TF (1m, 3m, 5m, 10m, 15m, 30m, 60m).
* Lane 1/2/3/4 (Length, Type, Color, Width, Dash): Choose SMA, EMA, WMA and the look you want.
* Show/Hide per Lane: Toggle each MA independently.
* Cloud Settings: Enable/disable; choose Top MA and Bottom MA from the lanes. **Coming Soon**
* Flip Cues: On/off; choose which MA to watch for crosses and where to plot the marker.
* Bars Required: Minimum bars before plotting to avoid partial/invalid feeds on fresh charts.

Names may differ slightly depending on your build; the intent is the same.

**How it works (plain English)**

NinjaTrader lets indicators read data from another timeframe. MTF MMA adds one or more AddDataSeries calls under the hood and calculates your chosen moving averages on that series. Those values are then drawn on your active chart with smart syncing so the lines align with your current candles. *When clouds are on, the area between two selected MAs gets filled.*

**Tips & gotchas**

* Give it bars: If you point to a higher TF (e.g., 60m) on a fresh chart, there won’t be enough bars at first. Let the chart load or scroll back.

* BarsRequiredToPlot: If you see an “index out of range” on first load, increase this setting a bit so the indicator waits until all inputs are ready.
* Cloud on MTF: Clouds work fine on MTF feeds, but the first few bars of a session can look stepped while the higher TF completes its first candle. **Coming Soon**
* Performance: More lanes + clouds + flip cues = more draw calls. Start lean, then add what you need.

**Versioning & updates**

* Semantic versioning: major.minor.patch (e.g., 1.2.0)
* The indicator includes a lightweight update check. If a new build is posted, you’ll get a heads‑up in NinjaTrader with a link to the changelog.
* No auto‑updates are installed for you; you always import updates yourself so you keep control.

**Changelog (summary)**

* 1.0.0.0 – Initial public release: 4 lanes, MTF source.
* 1.1.0.0 - Feature adds: Change to user licensing model, add lightweight update check.

**FAQ**

* Does this repaint? No. It reads higher‑TF data that finalizes when that candle closes. Until then, like any live bar, values can evolve in real‑time.
* Can I alert on crosses? The current release focuses on visuals; alerts are on the roadmap. For now, use flip cues as a visual prompt.
* Can I use this with strategies? Yes—plotting indicators can be referenced by strategies. This package itself does not place trades.
* Prop‑firm friendly? It’s an indicator, so it’s neutral. It can help keep your bias clean (e.g., above/below VWAP) which many rule sets prefer.

**License**

Commercial license, single user unless otherwise noted on your receipt. You’re free to use it on as many charts/instruments as you like. Redistribution of the source or compiled assemblies is not permitted.

**Support**

* Docs & updates: https://www.badbuddhacustoms.com
* Email: support@badbuddhacustoms.com

* When you reach out, include:

    * NinjaTrader version (Help → About)
    * Your instrument + timeframe
    * Indicator settings screenshot
    * Any error text from New → Log