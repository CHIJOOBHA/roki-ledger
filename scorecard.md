# Roki scorecard

Updated 2026-11-08 from the full paper record since 2026-10-22 (real prices, real costs, paper money). From Roki's live record, the same one the dashboard shows. Brain version `e63a54e348dd979a` (approved 2026-10-26).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. Roki changes itself only within fixed limits (it can switch trades off and back on, never add rules or size), after 40+ trades for a rule, and every change is a public dated commit.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Breakout | crypto | 72 | 28 | −$199.59 | -0.28% | 0.20% | Change proposed |
| Gap fade | US stock | 27 | 14 | −$0.09 | -0.00% | 0.13% | On track |
| Extreme-close fade | IN stock | 13 | 7 | −₹2,584 | -0.20% | 0.11% | Too early |
| Extreme-close fade | IN index | 11 | 2 | −₹5,067 | -0.46% | 0.04% | Too early |
| Extreme-close fade | crypto | 9 | 5 | +$65.95 | 0.73% | 0.05% | Too early |
| Big-gap fade | US stock | 8 | 4 | +$67.05 | 0.84% | 0.60% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 118 | 89 | 75% | 71%–76% |
| Night before: will yesterday's low break? | 119 | 76 | 64% | 71%–76% |
| At the open: will the gap fill? | 180 | 141 | 78% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 142 | 109 | 77% | 72%–75% |

All markets: 415 of 559 calls right (74%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

9 of 13 right (69%). Gold: 1 of 1, India: 8 of 12.


## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | India listed to 2026-12-31, US to 2027-12-31. | agrees |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 16 of 60 winners went against Roki first (27%). | differs |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | 14 of 36 losing fade trades came on one-way days or hit the safety stop. | agrees |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 9 of 27 gap-fade days touched yesterday's close (33%). | agrees |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 22 of 140 trades were up and then gave it back (16%). | agrees |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average 0.06% a trade (39 trades) vs 0.16% on normal days (48). | agrees |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 89 of 118 (75%). | agrees |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 76 of 119 (64%). | agrees |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 141 of 180 (78%). | agrees |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 109 of 142 (77%). | agrees |

## 4. Proposed rule changes

- Move Breakout in crypto to learning-only: 72 trades averaging -0.28% against 0.20% in testing. (Roki acts on it at its weekly self-check)

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-11-07 | 3 | 1 | −$14.39 | 0/0 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-11-06 | 7 | 5 | +$80.05 | 29/38 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-11-05 | 14 | 10 | −₹2,009 · +$214.42 | 29/44 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-11-04 | 19 | 5 | −₹5,038 · −$114.83 | 44/52 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-03 | 12 | 3 | −₹5,892 · −$10.13 | 45/54 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-02 | 12 | 4 | +₹2,386 · −$64.89 | 31/47 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |
| 2026-11-01 | 1 | 1 | +$4.27 | 0/0 | A win like this is expected about half the time or a bit more. The rule only pays over many trades, so Roki keeps the size the same every day. |

## 7. Same decision, different result

Every closed trade is compared with the most similar earlier trade of the same decision (same rule, market and side) that had the opposite result. Things Roki could see before entering are possible filters; things seen only after entering explain the result but can't be used to decide.

282 comparisons so far. In 51 of them nothing Roki could see before entering was different (normal luck for the rule).

- **2026-11-06 · Gap fade (late entry): buy SILVER (learning-only):** Same decision (Gap fade (late entry): buy SILVER) made +$0.77 on 2026-11-06 and −$1.94 on 2026-10-23. Before entry the two days looked the same. After entry: the price came back to yesterday's close on the winning day only. Nothing Roki could see before entering was different, so this looks like the rule's normal luck, not a mistake.
- **2026-11-06 · Gap fade (late entry): buy US stock (AAPL and NVDA) (learning-only):** Same decision (Gap fade (late entry): buy US stock (AAPL and NVDA)) made +$3.45 on 2026-11-06 and −$29.45 on 2026-11-05. Before entry: the trade was with the 50-day trend on the winning day, the trade was against the 50-day trend on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the losing day was a one-way trend day; the other was not; the day's move ran against the trade on the losing day only; the day's range was 0.9× normal on the winning day and 2.6× on the losing day; the price came back to yesterday's close on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-06 · Gap fade (late entry): buy US index (DOW and S&P 500) (learning-only):** Same decision (Gap fade (late entry): buy US index (DOW and S&P 500)) made +$1.96 on 2026-11-06 and −$4.39 on 2026-10-22. Before entry: opened 0.66× a normal day below yesterday's close on the winning day, opened 0.96× a normal day below yesterday's close on the losing day; the market was lively (1.42× its usual range) on the winning day, the market was normal (1.13× its usual range) on the losing day; yesterday's range was 4.48× normal on the winning day, yesterday's range was 0.96× normal on the losing day; yesterday closed at 2% of its range on the winning day, yesterday closed at 78% of its range on the losing day; the trade was against the 50-day trend on the winning day, the trade was with the 50-day trend on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the price came back to yesterday's close on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-06 · Gap fade (late entry): buy US stock (MSFT and NVDA) (learning-only):** Same decision (Gap fade (late entry): buy US stock (MSFT and NVDA)) made +$11.17 on 2026-11-06 and −$29.45 on 2026-11-05. Before entry: the market was lively (1.40× its usual range) on the winning day, the market was normal (1.08× its usual range) on the losing day; yesterday's range was 1.77× normal on the winning day, yesterday's range was 1.34× normal on the losing day; the trade was with the 50-day trend on the winning day, the trade was against the 50-day trend on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the losing day was a one-way trend day; the other was not; the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 0.9× normal on the winning day and 2.6× on the losing day; the price came back to yesterday's close on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-06 · Gap fade (late entry): sell US stock (NVDA and JPM) (learning-only):** Same decision (Gap fade (late entry): sell US stock (NVDA and JPM)) made +$34.60 on 2026-11-06 and −$13.74 on 2026-11-04. Before entry: the market was normal (1.19× its usual range) on the winning day, the market was normal (0.80× its usual range) on the losing day; yesterday's range was 2.66× normal on the winning day, yesterday's range was 1.01× normal on the losing day; yesterday closed at 1% of its range on the winning day, yesterday closed at 44% of its range on the losing day; Friday on the winning day, Wednesday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.5× normal on the winning day and 2.1× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-07 · Extreme-close fade: buy crypto (BTC and SOL):** Same decision (Extreme-close fade: buy crypto (BTC and SOL)) made +$1.49 on 2026-10-31 and −$5.89 on 2026-11-07. Before entry: yesterday's range was 1.15× normal on the winning day, yesterday's range was 0.51× normal on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-07 · Extreme-close fade: buy crypto (BTC and XRP):** Same decision (Extreme-close fade: buy crypto (BTC and XRP)) made +$6.50 on 2026-11-03 and −$14.91 on 2026-11-07. Before entry: yesterday closed at 5% of its range on the winning day, yesterday closed at 12% of its range on the losing day; Tuesday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-11-07 · Breakout: sell XRP:** Same decision (Breakout: sell XRP) made +$6.40 on 2026-11-07 and −$13.14 on 2026-10-24. Before entry the two days looked the same. After entry: the day's move ran against the trade on the losing day only. Nothing Roki could see before entering was different, so this looks like the rule's normal luck, not a mistake.

## 8. Patterns from those comparisons, tested on new trades only

A pattern is written down the day it is found (in `learning/patterns.json`) and judged only on trades closed after that day, because any idea looks good on the data it came from.

| Rule | Market | When | Found | Then (inside vs rest) | Since (inside vs rest) | Status |
|---|---|---|---|---|---|---|
| Gap fade (late entry) | US stock | the day before was big | 2026-11-08 | 1.22% (8) vs -0.73% (15) | - | Watching |
| Gap fade (late entry) | US stock | the trade was with the longer trend | 2026-11-08 | 0.69% (13) vs -1.01% (10) | - | Watching |
| Gap fade (late entry) | US stock | the trade was against the longer trend | 2026-11-08 | -1.01% (10) vs 0.69% (13) | - | Watching |
| Gap fade | US stock | the day before was big | 2026-11-08 | 0.95% (10) vs -0.56% (17) | - | Watching |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
