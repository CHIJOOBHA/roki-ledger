# Roki scorecard

Updated 2026-11-01 from the full paper record since 2026-10-22 (real prices, real costs, paper money). From Roki's live record, the same one the dashboard shows. Brain version `e63a54e348dd979a` (approved 2026-10-26).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. Roki changes itself only within fixed limits (it can switch trades off and back on, never add rules or size), after 40+ trades for a rule, and every change is a public dated commit.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Breakout | crypto | 41 | 15 | −$116.66 | -0.28% | 0.20% | On track |
| Gap fade | US stock | 10 | 4 | −$38.24 | -0.38% | 0.13% | Too early |
| Extreme-close fade | IN stock | 8 | 6 | +₹1,880 | 0.24% | 0.11% | Too early |
| Big-gap fade | US stock | 5 | 2 | −$8.38 | -0.17% | 0.60% | Too early |
| Extreme-close fade | crypto | 4 | 2 | +$2.12 | 0.05% | 0.05% | Too early |
| Extreme-close fade | IN index | 4 | 2 | +₹1,021 | 0.26% | 0.04% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 70 | 45 | 64% | 71%–76% |
| Night before: will yesterday's low break? | 68 | 44 | 65% | 71%–76% |
| At the open: will the gap fill? | 105 | 88 | 84% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 81 | 60 | 74% | 72%–75% |

All markets: 237 of 324 calls right (73%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

9 of 13 right (69%). Gold: 1 of 1, India: 8 of 12.


## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | India listed to 2026-12-31, US to 2027-12-31. | agrees |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 10 of 31 winners went against Roki first (32%). | agrees |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | 5 of 15 losing fade trades came on one-way days or hit the safety stop. | early |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 1 of 10 gap-fade days touched yesterday's close (10%). | early |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 16 of 72 trades were up and then gave it back (22%). | agrees |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average 0.35% a trade (25 trades) vs 0.33% on normal days (22). | differs |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 45 of 70 (64%). | agrees |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | Right 44 of 68 (65%). | agrees |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 88 of 105 (84%). | agrees |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 60 of 81 (74%). | agrees |

## 4. Proposed rule changes

None. No rule has met the agreed condition (live average below zero after 40+ counted trades).

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-10-31 | 3 | 1 | −$9.11 | 0/0 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-10-30 | 8 | 3 | −$34.19 | 30/36 | Breakouts often fail and snap back. In crypto the rule pays only over many trades, so occasional stops are expected. |
| 2026-10-29 | 15 | 9 | +₹624 · +$55.72 | 40/56 | Breakouts often fail and snap back. In crypto the rule pays only over many trades, so occasional stops are expected. |
| 2026-10-28 | 7 | 3 | +₹1,236 · +$2.71 | 35/51 | On quiet days the move is smaller than the charges. That is why Roki skips quiet markets for the extreme-close rule. |
| 2026-10-27 | 11 | 4 | −₹681 · −$4.17 | 26/30 | The day kept going in yesterday's direction. Roki's edge is small (a few tenths of a percent per trade), so runs of days like this happen and are survived by keeping each trade small. |
| 2026-10-26 | 4 | 3 | −$3.62 | 33/53 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-25 | 3 | 3 | +$14.35 | 0/0 | A win like this is expected about half the time or a bit more. The rule only pays over many trades, so Roki keeps the size the same every day. |

## 7. Same decision, different result

Every closed trade is compared with the most similar earlier trade of the same decision (same rule, market and side) that had the opposite result. Things Roki could see before entering are possible filters; things seen only after entering explain the result but can't be used to decide.

117 comparisons so far. In 31 of them nothing Roki could see before entering was different (normal luck for the rule).

- **2026-10-30 · Breakout: sell US stock (JPM and MSFT) (learning-only):** Same decision (Breakout: sell US stock (JPM and MSFT)) made +$15.14 on 2026-10-30 and −$6.64 on 2026-10-28. Before entry: opened 0.34× a normal day above yesterday's close on the winning day, opened 0.08× a normal day above yesterday's close on the losing day; Friday on the winning day, Wednesday on the losing day. After entry: the winning day was a one-way trend day; the other was not; the day's range was 2.0× normal on the winning day and 0.8× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-30 · Gap fade (late entry): buy S&P 500 (learning-only):** Same decision (Gap fade (late entry): buy S&P 500) made +$0.81 on 2026-10-29 and −$8.44 on 2026-10-30. Before entry: opened 0.66× a normal day below yesterday's close on the winning day, opened 1.42× a normal day below yesterday's close on the losing day; Thursday on the winning day, Friday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 0.6× normal on the winning day and 1.8× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-30 · Gap fade (late entry): buy AMZN (learning-only):** Same decision (Gap fade (late entry): buy AMZN) made +$4.88 on 2026-10-30 and −$3.95 on 2026-10-29. Before entry: opened 1.87× a normal day below yesterday's close on the winning day, opened 1.30× a normal day below yesterday's close on the losing day; yesterday's range was 1.33× normal on the winning day, yesterday's range was 0.54× normal on the losing day; yesterday closed at 32% of its range on the winning day, yesterday closed at 78% of its range on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the winning day was a one-way trend day; the other was not; the day's move ran against the trade on the losing day only; the price went against Roki first on the winning day only; the day's range was 2.0× normal on the winning day and 1.3× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-30 · Gap fade (late entry): buy SILVER (learning-only):** Same decision (Gap fade (late entry): buy SILVER) made +$2.14 on 2026-10-29 and −$0.52 on 2026-10-30. Before entry: opened 1.97× a normal day below yesterday's close on the winning day, opened 2.42× a normal day below yesterday's close on the losing day; yesterday closed at 98% of its range on the winning day, yesterday closed at 51% of its range on the losing day; Thursday on the winning day, Friday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-30 · Gap fade (late entry): buy US stock (AAPL and NVDA) (learning-only):** Same decision (Gap fade (late entry): buy US stock (AAPL and NVDA)) made +$2.10 on 2026-10-26 and −$23.95 on 2026-10-30. Before entry: opened 0.64× a normal day below yesterday's close on the winning day, opened 0.97× a normal day below yesterday's close on the losing day; the trade was with the 50-day trend on the winning day, the trade was against the 50-day trend on the losing day; Monday on the winning day, Friday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.0× normal on the winning day and 1.6× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-30 · Breakout: sell DOW (learning-only):** Same decision (Breakout: sell DOW) made +$5.79 on 2026-10-30 and −$2.57 on 2026-10-27. Before entry: yesterday closed at 80% of its range on the winning day, yesterday closed at 28% of its range on the losing day; Friday on the winning day, Tuesday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.8× normal on the winning day and 0.5× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-31 · Extreme-close fade on a skip day: buy XRP (learning-only):** Same decision (Extreme-close fade on a skip day: buy XRP) made +$13.71 on 2026-10-30 and −$5.67 on 2026-10-31. Before entry: yesterday's range was 2.09× normal on the winning day, yesterday's range was 1.25× normal on the losing day; yesterday closed at 1% of its range on the winning day, yesterday closed at 82% of its range on the losing day; Friday on the winning day, Saturday on the losing day. After entry: the day's move ran against the trade on the losing day only; the day's range was 1.4× normal on the winning day and 0.4× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-31 · Breakout: sell SOL:** Same decision (Breakout: sell SOL) made +$35.43 on 2026-10-29 and −$0.07 on 2026-10-31. Before entry: yesterday's range was 0.95× normal on the winning day, yesterday's range was 1.49× normal on the losing day; Thursday on the winning day, Saturday on the losing day. After entry: the winning day was a one-way trend day; the other was not; the day's range was 2.4× normal on the winning day and 0.5× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.

## 8. Patterns from those comparisons, tested on new trades only

A pattern is written down the day it is found (in `learning/patterns.json`) and judged only on trades closed after that day, because any idea looks good on the data it came from.

| Rule | Market | When | Found | Then (inside vs rest) | Since (inside vs rest) | Status |
|---|---|---|---|---|---|---|
| (none found yet) | | | | | | |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
