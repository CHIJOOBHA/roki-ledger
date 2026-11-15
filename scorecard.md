# Roki scorecard

Updated 2026-11-15 from the full paper record since 2026-10-22 (real prices, real costs, paper money). From Roki's live record, the same one the dashboard shows. Brain version `d63856a4b1f8032d` (approved 2026-11-08).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. Roki changes itself only within fixed limits (it can switch trades off and back on, never add rules or size), after 40+ trades for a rule, and every change is a public dated commit.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Breakout | crypto | 76 | 30 | −$162.62 | -0.21% | 0.20% | On track |
| Gap fade | US stock | 29 | 15 | +$17.32 | 0.24% | 0.13% | On track |
| Extreme-close fade | IN stock | 16 | 7 | −₹3,468 | -0.28% | 0.11% | Too early |
| Extreme-close fade | IN index | 15 | 4 | −₹6,615 | -0.48% | 0.04% | Too early |
| Extreme-close fade | crypto | 13 | 6 | +$47.66 | -0.09% | 0.05% | Too early |
| Big-gap fade | US stock | 9 | 5 | +$95.05 | 1.99% | 0.60% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 167 | 125 | 75% | 71%–76% |
| Night before: will yesterday's low break? | 166 | 108 | 65% | 71%–76% |
| At the open: will the gap fill? | 255 | 201 | 79% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 200 | 153 | 77% | 72%–75% |

All markets: 587 of 788 calls right (74%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

9 of 13 right (69%). Gold: 1 of 1, India: 8 of 12.


## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | India listed to 2026-12-31, US to 2027-12-31. | agrees |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 16 of 67 winners went against Roki first (24%). | differs |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | 18 of 45 losing fade trades came on one-way days or hit the safety stop. | agrees |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 10 of 29 gap-fade days touched yesterday's close (34%). | agrees |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 26 of 158 trades were up and then gave it back (16%). | agrees |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average 0.01% a trade (47 trades) vs -0.02% on normal days (67). | differs |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 125 of 167 (75%). | agrees |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 108 of 166 (65%). | agrees |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 201 of 255 (79%). | agrees |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 153 of 200 (77%). | agrees |

## 4. Proposed rule changes

None. No rule has met the agreed condition (live average below zero after 40+ counted trades).

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-11-14 | 1 | 0 | −$10.61 | 0/0 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-12 | 2 | 2 | +$56 | 33/42 | A win like this is expected about half the time or a bit more. The rule only pays over many trades, so Roki keeps the size the same every day. |
| 2026-11-11 | 2 | 0 | −₹1,048 · −$0.43 | 36/47 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-10 | 3 | 1 | −$17.83 | 21/33 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-09 | 6 | 2 | −₹1,383 | 44/52 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-11-08 | 4 | 2 | +$36.96 | 8/11 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-11-07 | 3 | 1 | −$14.39 | 0/0 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |

## 7. Same decision, different result

Every closed trade is compared with the most similar earlier trade of the same decision (same rule, market and side) that had the opposite result. Things Roki could see before entering are possible filters; things seen only after entering explain the result but can't be used to decide.

424 comparisons so far. In 81 of them nothing Roki could see before entering was different (normal luck for the rule).

- **2026-11-13 · Extreme-close fade on a skip day: buy US stock (MSFT and AMZN) (learning-only):** Same decision (Extreme-close fade on a skip day: buy US stock (MSFT and AMZN)) made +$12.41 on 2026-10-23 and −$3.12 on 2026-11-13. Before entry: opened 0.29× a normal day below yesterday's close on the winning day, opened 0.22× a normal day above yesterday's close on the losing day; the market was normal (0.99× its usual range) on the winning day, the market was lively (1.62× its usual range) on the losing day; yesterday's range was 1.24× normal on the winning day, yesterday's range was 0.66× normal on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-13 · Extreme-close fade on a skip day: buy DOW (learning-only):** Same decision (Extreme-close fade on a skip day: buy DOW) made +$3.57 on 2026-11-06 and −$2.03 on 2026-11-13. Before entry: opened 0.66× a normal day below yesterday's close on the winning day, opened 0.25× a normal day above yesterday's close on the losing day; yesterday's range was 4.48× normal on the winning day, yesterday's range was 0.63× normal on the losing day; the trade was against the 50-day trend on the winning day, the trade was with the 50-day trend on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-13 · Breakout: buy AAPL (learning-only):** Same decision (Breakout: buy AAPL) made +$2.09 on 2026-11-11 and −$3.30 on 2026-11-13. Before entry: Wednesday on the winning day, Friday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Nothing Roki could see before entering was different, so this looks like the rule's normal luck, not a mistake.
- **2026-11-13 · Extreme-close fade on a skip day: buy JPM (learning-only):** Same decision (Extreme-close fade on a skip day: buy JPM) made +$3.82 on 2026-11-06 and −$0.19 on 2026-11-13. Before entry: opened 0.58× a normal day below yesterday's close on the winning day, opened 0.44× a normal day above yesterday's close on the losing day; yesterday's range was 4.57× normal on the winning day, yesterday's range was 0.60× normal on the losing day; the trade was against the 50-day trend on the winning day, the trade was with the 50-day trend on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.2× normal on the winning day and 0.5× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-13 · Extreme-close fade on a skip day: buy US stock (MSFT and AAPL) (learning-only):** Same decision (Extreme-close fade on a skip day: buy US stock (MSFT and AAPL)) made +$12.41 on 2026-10-23 and −$1.78 on 2026-11-13. Before entry: opened 0.29× a normal day below yesterday's close on the winning day, opened 0.33× a normal day above yesterday's close on the losing day; the market was normal (0.99× its usual range) on the winning day, the market was lively (1.35× its usual range) on the losing day; yesterday's range was 1.24× normal on the winning day, yesterday's range was 0.54× normal on the losing day. After entry: the day's move ran against the trade on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-13 · Breakout: sell DOW (learning-only):** Same decision (Breakout: sell DOW) made +$5.79 on 2026-10-30 and −$1.04 on 2026-11-13. Before entry: the market was normal (1.07× its usual range) on the winning day, the market was lively (1.56× its usual range) on the losing day; yesterday closed at 80% of its range on the winning day, yesterday closed at 5% of its range on the losing day. After entry: the day's range was 1.8× normal on the winning day and 0.7× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-13 · Breakout: sell S&P 500 (learning-only):** Same decision (Breakout: sell S&P 500) made +$36.35 on 2026-11-05 and −$0.98 on 2026-11-13. Before entry: opened 0.15× a normal day below yesterday's close on the winning day, opened 0.21× a normal day above yesterday's close on the losing day; the market was lively (1.22× its usual range) on the winning day, the market was lively (1.80× its usual range) on the losing day; Thursday on the winning day, Friday on the losing day. After entry: the winning day was a one-way trend day; the other was not; the day's range was 4.9× normal on the winning day and 1.0× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-14 · Extreme-close fade: buy BTC:** Same decision (Extreme-close fade: buy BTC) made +$6.50 on 2026-11-03 and −$10.61 on 2026-11-14. Before entry: the market was normal (0.87× its usual range) on the winning day, the market was lively (1.28× its usual range) on the losing day; yesterday closed at 5% of its range on the winning day, yesterday closed at 16% of its range on the losing day; Tuesday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.

## 8. Patterns from those comparisons, tested on new trades only

A pattern is written down the day it is found (in `learning/patterns.json`) and judged only on trades closed after that day, because any idea looks good on the data it came from.

| Rule | Market | When | Found | Then (inside vs rest) | Since (inside vs rest) | Status |
|---|---|---|---|---|---|---|
| Gap fade (late entry) | US stock | the day before was big | 2026-11-08 | 1.22% (8) vs -0.73% (15) | -0.12% (1) vs 0.97% (5) | Watching |
| Gap fade (late entry) | US stock | the trade was with the longer trend | 2026-11-08 | 0.69% (13) vs -1.01% (10) | -1.30% (1) vs 1.21% (5) | Watching |
| Gap fade (late entry) | US stock | the trade was against the longer trend | 2026-11-08 | -1.01% (10) vs 0.69% (13) | 1.21% (5) vs -1.30% (1) | Watching |
| Gap fade | US stock | the day before was big | 2026-11-08 | 0.95% (10) vs -0.56% (17) | 3.90% (1) vs 1.35% (5) | Watching |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
