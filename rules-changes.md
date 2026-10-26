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
