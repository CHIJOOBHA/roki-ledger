# Roki scorecard

Updated 2026-11-22 from the full paper record since 2026-10-22 (real prices, real costs, paper money). Rebuilt from real prices because the live server answered 402; older sessions may be incomplete. Brain version `d63856a4b1f8032d` (approved 2026-11-08).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. Roki changes itself only within fixed limits (it can switch trades off and back on, never add rules or size), after 40+ trades for a rule, and every change is a public dated commit.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Gap fade | US stock | 2 | 2 | +$12.92 | 1.54% | 0.13% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 0 | 0 | - | 71%–76% |
| Night before: will yesterday's low break? | 0 | 0 | - | 71%–76% |
| At the open: will the gap fill? | 42 | 35 | 83% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 31 | 14 | 45% | 72%–75% |

All markets: 49 of 73 calls right (67%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

9 of 13 right (69%). Gold: 1 of 1, India: 8 of 12.


## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | Holiday list ends soon for India (add NSE's next-year list). | differs |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 2 of 2 winners went against Roki first (100%). | early |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | No losing fade trades yet. | early |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 2 of 2 gap-fade days touched yesterday's close (100%). | early |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 0 of 2 trades were up and then gave it back (0%). | early |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average -2.41% a trade (13 trades) vs -1.30% on normal days (4). | early |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 35 of 42 (83%). | agrees |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 14 of 31 (45%). | differs |

## 4. Proposed rule changes

None. No rule has met the agreed condition (live average below zero after 40+ counted trades).

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-11-20 | 1 | 1 | +$5.22 | 14/25 | This is the rule's edge: big gaps return to yesterday's close 6–8 points more often than distance alone predicts. One win proves nothing on its own; it counts as part of the long record. |
| 2026-11-19 | 1 | 1 | +$7.7 | 14/23 | This is the rule's edge: big gaps return to yesterday's close 6–8 points more often than distance alone predicts. One win proves nothing on its own; it counts as part of the long record. |

## 7. Same decision, different result

Every closed trade is compared with the most similar earlier trade of the same decision (same rule, market and side) that had the opposite result. Things Roki could see before entering are possible filters; things seen only after entering explain the result but can't be used to decide.

22 comparisons so far. In 4 of them nothing Roki could see before entering was different (normal luck for the rule).

- **2026-11-20 · Breakout: buy SENSEX (learning-only):** Same decision (Breakout: buy SENSEX) made +₹837 on 2026-11-20 and −₹267 on 2026-11-19. Before entry: opened 0.56× a normal day below yesterday's close on the winning day, opened right at yesterday's close on the losing day; yesterday's range was 1.47× normal on the winning day, yesterday's range was 0.86× normal on the losing day; yesterday closed at 98% of its range on the winning day, yesterday closed at 32% of its range on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the winning day was a one-way trend day; the other was not. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-20 · Breakout: sell US OIL (learning-only):** Same decision (Breakout: sell US OIL) made +$8.22 on 2026-11-18 and −$5.43 on 2026-11-20. Before entry: yesterday closed at 34% of its range on the winning day, yesterday closed at 67% of its range on the losing day; Wednesday on the winning day, Friday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-20 · Breakout: buy IN stock (HDFCBANK and RELIANCE) (learning-only):** Same decision (Breakout: buy IN stock (HDFCBANK and RELIANCE)) made +₹269 on 2026-11-19 and −₹268 on 2026-11-20. Before entry: opened 0.06× a normal day below yesterday's close on the winning day, opened 0.43× a normal day below yesterday's close on the losing day; yesterday's range was 0.70× normal on the winning day, yesterday's range was 1.43× normal on the losing day; yesterday closed at 32% of its range on the winning day, yesterday closed at 79% of its range on the losing day; Thursday on the winning day, Friday on the losing day. After entry: the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-21 · Breakout: sell BNB (learning-only):** Same decision (Breakout: sell BNB) made +$15.34 on 2026-11-20 and −$8.27 on 2026-11-21. Before entry: yesterday's range was 0.67× normal on the winning day, yesterday's range was 1.97× normal on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-21 · Breakout: sell BTC (learning-only):** Same decision (Breakout: sell BTC) made +$9.96 on 2026-11-20 and −$10.80 on 2026-11-21. Before entry: yesterday's range was 0.92× normal on the winning day, yesterday's range was 1.64× normal on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-21 · Breakout: sell ETH (learning-only):** Same decision (Breakout: sell ETH) made +$16.15 on 2026-11-20 and −$18.36 on 2026-11-21. Before entry: yesterday's range was 0.75× normal on the winning day, yesterday's range was 1.75× normal on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-21 · Breakout: sell SOL (learning-only):** Same decision (Breakout: sell SOL) made +$11.33 on 2026-11-20 and −$11.75 on 2026-11-21. Before entry: yesterday's range was 0.74× normal on the winning day, yesterday's range was 1.39× normal on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-21 · Breakout: sell XRP (learning-only):** Same decision (Breakout: sell XRP) made +$11.19 on 2026-11-20 and −$13.56 on 2026-11-21. Before entry: yesterday's range was 0.78× normal on the winning day, yesterday's range was 1.62× normal on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.

## 8. Patterns from those comparisons, tested on new trades only

A pattern is written down the day it is found (in `learning/patterns.json`) and judged only on trades closed after that day, because any idea looks good on the data it came from.

| Rule | Market | When | Found | Then (inside vs rest) | Since (inside vs rest) | Status |
|---|---|---|---|---|---|---|
| Gap fade (late entry) | US stock | the day before was big | 2026-11-08 | 1.22% (8) vs -0.73% (15) | - | Watching |
| Gap fade (late entry) | US stock | the trade was with the longer trend | 2026-11-08 | 0.69% (13) vs -1.01% (10) | 2.81% (1) vs 0.23% (1) | Watching |
| Gap fade (late entry) | US stock | the trade was against the longer trend | 2026-11-08 | -1.01% (10) vs 0.69% (13) | 0.23% (1) vs 2.81% (1) | Watching |
| Gap fade | US stock | the day before was big | 2026-11-08 | 0.95% (10) vs -0.56% (17) | - | Watching |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
