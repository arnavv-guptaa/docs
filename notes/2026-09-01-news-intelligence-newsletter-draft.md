# News that knows what you hold

*Newsletter draft, 1 September 2026. Internal working draft: needs compliance review before any distribution.*

**COMPLIANCE: needs disclaimer (do not distribute without the compliance pass)**

In 1971, Herbert Simon warned that a wealth of information creates a poverty of attention. He was writing about managers with too much paper on their desks. He had not seen a modern portfolio manager's morning: filings, wires, broker notes, and alerts arriving faster than anyone can read them, across more names than any team can follow. For most of market history the edge went to whoever got the news first. Couriers lost to telegraphs, telegraphs lost to the stock ticker, tickers lost to terminals. Today the news arrives everywhere at once, so the edge has moved to a different question: of everything that just happened, what actually touches my portfolio?

Most news tools stop short of that question. A good automated summary tells you what happened, and tells you quickly. But the summary leaves the expensive work to you: deciding whether the event touches anything you own, in which direction, and by roughly how much. That judgment is where the hours go. It is also the part of the job that scales worst, because a watchlist grows faster than a reading day does.

## What we built

News Intelligence, part of the Parallax platform, closes that gap. It monitors company disclosures and news sources across major Asian and US equity markets, continuously and automatically, and runs every detected event through the same sequence before anything reaches you.

When something breaks, keyword and relevance scoring flags it. A relevance and freshness check then discards the stale, the duplicated, and the immaterial; many items stop here, by design. Each event that survives gets a scenario analysis for the affected stock: a bull case, a base case, and a bear case, each with an estimated price impact and an assigned probability. Then comes the step that summaries skip. The assessed impact is reconciled against actual portfolio holdings, including look-through into ETF constituents. If a company you have never researched sits inside an ETF you hold and something happens to it, you find out. If an event touches nothing you own, directly or indirectly, it does not reach your alerts.

Results are delivered to the people holding the affected positions through reports, dashboards, and alerts, with narrative context that explains the scenario math rather than compressing it into a single score.

## Why trust an automated pipeline

A fair question, since no editor reviews each item by hand. Our answer is the discipline of the system. Every item passes through the same detection, validation, and assessment sequence, so the process is repeatable and auditable. The same event and the same portfolio produce the same assessment, every time. The pipeline was built by the research team behind Parallax's factor scoring and valuation systems, and it holds to the standard we apply there, with assumptions stated, logic traceable, and no black boxes. Because the scenario structure is explicit, you can disagree with a probability and still use the framework. We would rather show you reasoning you can challenge than a score you have to take on faith.

Two things we are not claiming. News Intelligence does not predict returns, and it does not make decisions; it monitors, detects, assesses, and surfaces, while judgment stays with you. And coverage today centers on major Asian and US equity markets, where our research depth is greatest. We would rather be precise there than shallow everywhere.

## See it against your own portfolio

News Intelligence is live in the Parallax Console. The methodology, including how events are validated before they surface, is documented at [docs.chicago.global](https://docs.chicago.global/methodology/news-intelligence). If you want to see what it says about the portfolio you actually hold, reply to this note and we will set it up against your positions.

---

*The information and opinions in this report were prepared or are disseminated by **Chicago Global Capital Pte Ltd**, regulated by the **Monetary Authority of Singapore**.*

*This report is **not intended to, and does not, constitute an offer or solicitation** to buy and sell securities or engage in any investment activity. This report is for **informational purposes only**.*

*Statements in this report are not made with respect to any particular investor or type of investor. Securities, financial instruments, or strategies mentioned herein may not be suitable for all investors, and this material is not intended for any specific investor and does not take into account an investor's particular investment objectives, financial situations, or needs.*

*Chicago Global Capital recommends that investors **independently evaluate particular investments and strategies**.*
