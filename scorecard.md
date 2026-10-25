# Roki scorecard

Updated 2026-10-25 from the full paper record since 2026-10-22 (real prices, real costs, paper money). Brain version `e63a54e348dd979a` (approved 2026-10-22).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. A rule is only changed after 40+ trades, and only when the owner approves.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Breakout | crypto | 10 | 2 | −$76.52 | -0.77% | 0.20% | Too early |
| Gap fade | US stock | 3 | 0 | −$53.45 | -1.78% | 0.13% | Too early |
| Extreme-close fade | IN stock | 2 | 2 | +₹1,863 | 0.93% | 0.11% | Too early |
| Big-gap fade | US stock | 1 | 0 | −$25.08 | -2.51% | 0.60% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 0 | 0 | - | 71%–76% |
| Night before: will yesterday's low break? | 0 | 0 | - | 71%–76% |
| At the open: will the gap fill? | 27 | 22 | 81% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 23 | 18 | 78% | 72%–75% |

All markets: 40 of 50 calls right (80%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

None scored yet.
1 locked calls are still waiting for their session. India calls count only once they are published (30+ days after the session, under SEBI's rule).

## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | India listed to 2026-12-31, US to 2027-12-31. | agrees |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 0 of 4 winners went against Roki first (0%). | early |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | 3 of 4 losing fade trades came on one-way days or hit the safety stop. | early |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 0 of 3 gap-fade days touched yesterday's close (0%). | early |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 6 of 16 trades were up and then gave it back (38%). | early |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average 0.86% a trade (8 trades) vs 1.55% on normal days (4). | early |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 22 of 27 (81%). | early |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 18 of 23 (78%). | early |

## 4. Proposed rule changes

None. No rule has met the agreed condition (live average below zero after 40+ counted trades).

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-10-24 | 5 | 0 | −$44.4 | 0/0 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-23 | 6 | 2 | −$36.61 | 19/24 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-22 | 5 | 2 | +₹1,863 · −$74.04 | 21/26 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
