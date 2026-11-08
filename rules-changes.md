# Changes to Roki's brain

Every approved change to rules, costs, expectations or data limits, newest last.

| Date | Fingerprint | What changed |
|---|---|---|
| 2026-10-22 | e63a54e348dd979a | Baseline: each market's real costs and currency; gap fade on Indian indices learning-only; data guard limits |
| 2026-10-26 | e63a54e348dd979a | Data cross-check: bad 5-minute prints beyond the day's own range are dropped; a market whose daily and 5-minute bars disagree by more than 1% is skipped. Self-control added (empty): Roki may switch trades off and back on by itself, never add rules, markets or size. |
| 2026-10-26 | e63a54e348dd979a | Data guard: the newest daily bar may still be forming, so a close just outside its range is no longer an error (it had blocked crypto all day on 26 Oct 2026). |
| 2026-10-26 | e63a54e348dd979a | Owner's market list (26 Oct 2026): gold, silver, US oil, crypto, 5 US stocks, 5 Indian stocks, Nifty 50, Bank Nifty, Sensex. The S&P 500 is no longer traded or called, only read for its overnight move. At most 2 counted trades per market per day; any further entry is kept as learning-only. |
| 2026-10-26 | e63a54e348dd979a | S&P 500 and Dow added back at the owner's request, as learning-only (no rule passed Roki's 5-year test on US indices: every rule was below zero after costs in 2024-26). Their paper trades are mirrored as modelled SPY and DIA options. |
| 2026-10-26 | e63a54e348dd979a | Paper options account: up to 2 option trades a day in each Indian index and stock (Roki's per-market limit) instead of 1 a day in total. A live account keeps its own 1-a-day limit. |
| 2026-11-08 | 4da319c64893a349 | Roki self-control: Retired Breakout in crypto (now learning-only): 72 counted trades averaging -0.28% against 0.20% in testing. |
| 2026-11-08 | fa3bcacdd800fb46 | Portfolio risk desk added: once today's counted trades across all markets are down 2% together, new trades that day are learning-only; at most 3 counted same-direction entries per market group per day (markets that move together count as one bet). Rules, costs and sizes unchanged. |
| 2026-11-08 | 2c69777fc169da76 | Roki self-research: Found a new rule to try: "Opposite of: Small gap fill" in US indices (idea bank). It made money after costs in both halves of 5 years (+0.17% and +0.12% a trade). It now trades as learning-only until 30 live trades show whether it holds. |
| 2026-11-08 | d63856a4b1f8032d | Position sizing and drawdown brake: each trade is sized so its safety stop loses about 1% of its paper size (0.25x to 2x), so every market risks the same; counted trades are half size from a 5% drawdown of the counted record (reference account of 10 paper sizes) and pause from 10% until it recovers. Self-research adds a luck check across all tests (Benjamini-Hochberg 5%). Rules and costs unchanged. |
