# Roki scorecard

Updated 2026-10-26 from the full paper record since 2026-10-22 (real prices, real costs, paper money). Brain version `e63a54e348dd979a` (approved 2026-10-26).
Not investment advice. Small samples are mostly luck: a rule needs about 20 trades for a first look and 40 for a verdict.

## 1. Rules against their testing

Learning means a rule's live results move toward (or away from) what 5 years of testing said. Roki changes itself only within fixed limits (it can switch trades off and back on, never add rules or size), after 40+ trades for a rule, and every change is a public dated commit.

| Rule | Market | Trades | Won | Result | Avg per trade | Tested | Status |
|---|---|---|---|---|---|---|---|
| Breakout | crypto | 7 | 0 | −$55.58 | -0.79% | 0.20% | Too early |
| Gap fade | US stock | 3 | 0 | −$53.45 | -1.78% | 0.13% | Too early |
| Extreme-close fade | IN stock | 2 | 2 | +₹1,863 | 0.93% | 0.11% | Too early |
| Big-gap fade | US stock | 1 | 0 | −$25.08 | -2.51% | 0.60% | Too early |

## 2. Predictions against their testing

| Question | Calls scored | Right | Hit rate | Tested |
|---|---|---|---|---|
| Night before: will yesterday's high break? | 0 | 0 | - | 71%–76% |
| Night before: will yesterday's low break? | 0 | 0 | - | 71%–76% |
| At the open: will the gap fill? | 31 | 27 | 87% | 77%–78% |
| At the open: which side of yesterday's close will it end? | 26 | 17 | 65% | 72%–75% |

All markets: 44 of 57 calls right (77%). Calls are made only at 60% or more either way. Night-before calls are locked in `predictions/` before their session.

### Calls locked in public before their session

None scored yet.
13 locked calls are still waiting for their session.

## 3. Findings from testing, re-measured live

| Check | From testing | Live | Status |
|---|---|---|---|
| Market calendars are up to date | Each market keeps its own holidays and early closes (NSE, NYSE, CME). A missing holiday makes Roki wait for a session that never opens. | India listed to 2026-12-31, US to 2027-12-31. | agrees |
| Winners often go against Roki first | About half of winning gap fades first moved against the entry (by 0.29 of a day's range on average). This is why Roki uses wide stops. | 0 of 2 winners went against Roki first (0%). | early |
| Fade trades lose most on one-way days | Gap fades lose on trend days (range above 1.5 normal days). No filter found in testing could avoid these days in advance. | 3 of 4 losing fade trades came on one-way days or hit the safety stop. | early |
| Big gaps come back to yesterday's close about 3 times in 10 | When the open is more than half a normal day away from yesterday's close, the price touches that close roughly 30-34% of the time; that is the rule's target. | 0 of 3 gap-fade days touched yesterday's close (0%). | early |
| Holding to the close costs some winners | Taking profit early or tight stops made every rule worse in testing, so Roki holds to the close and accepts that some trades that were up end down. | 7 of 13 trades were up and then gave it back (54%). | early |
| Skip days are worse than normal days | Extreme-close fades on quiet markets, after small days, on Fridays and Sundays lost on new data (−0.12% a trade), so Roki skips them and only records them. | Skip days average 0.69% a trade (10 trades) vs 1.55% on normal days (4). | early |
| Night before: will yesterday's high break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| Night before: will yesterday's low break? | Right 71-76% of the time over 5 years of walk-forward testing. | No scored calls yet. | early |
| At the open: will the gap fill? | Right 77-78% of the time over 5 years of walk-forward testing. | Right 27 of 31 (87%). | agrees |
| At the open: which side of yesterday's close will it end? | Right 72-75% of the time over 5 years of walk-forward testing. | Right 17 of 26 (65%). | early |

## 4. Proposed rule changes

None. No rule has met the agreed condition (live average below zero after 40+ counted trades).

## 5. Last 7 trading days

| Day | Trades | Won | Result | Predictions | Lesson |
|---|---|---|---|---|---|
| 2026-10-25 | 2 | 0 | −$11.18 | 0/0 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-24 | 5 | 0 | −$44.4 | 0/0 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-23 | 1 | 0 | −$4.49 | 18/22 | Roki holds to the close on purpose: in testing, taking profit early or using tight stops cut the winners more than it saved, so some trades that were up end down. |
| 2026-10-22 | 5 | 2 | +₹1,863 · −$74.04 | 20/25 | Fades lose on strong one-way days. Roki tested filters to spot these days in advance; none held up on new data, so these losses are accepted as the rule's cost. |

## 7. Same decision, different result

Every closed trade is compared with the most similar earlier trade of the same decision (same rule, market and side) that had the opposite result. Things Roki could see before entering are possible filters; things seen only after entering explain the result but can't be used to decide.

7 comparisons so far. In 0 of them nothing Roki could see before entering was different (normal luck for the rule).

- **2026-10-23 · Breakout: buy commodity (US OIL and GOLD) (learning-only):** Same decision (Breakout: buy commodity (US OIL and GOLD)) made +$30.65 on 2026-10-23 and −$14.87 on 2026-10-22. Before entry: the market was normal (1.07× its usual range) on the winning day, the market was quiet (0.64× its usual range) on the losing day; yesterday closed at 56% of its range on the winning day, yesterday closed at 97% of its range on the losing day; the trade was with the 50-day trend on the winning day, the trade was against the 50-day trend on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the losing day was a one-way trend day; the other was not; the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.2× normal on the winning day and 2.1× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-23 · Breakout: sell BANK NIFTY (learning-only):** Same decision (Breakout: sell BANK NIFTY) made +₹246 on 2026-10-23 and −₹489 on 2026-10-22. Before entry: opened 0.08× a normal day above yesterday's close on the winning day, opened 0.35× a normal day below yesterday's close on the losing day; yesterday's range was 0.95× normal on the winning day, yesterday's range was 1.85× normal on the losing day; yesterday closed at 69% of its range on the winning day, yesterday closed at 24% of its range on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the day's move ran against the trade on the losing day only; the day's range was 1.5× normal on the winning day and 0.9× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-23 · Breakout: sell HDFCBANK (learning-only):** Same decision (Breakout: sell HDFCBANK) made +₹502 on 2026-10-22 and −₹637 on 2026-10-23. Before entry: opened 0.40× a normal day below yesterday's close on the winning day, opened 0.07× a normal day below yesterday's close on the losing day; Thursday on the winning day, Friday on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-23 · Gap fade: buy SILVER (learning-only):** Same decision (Gap fade: buy SILVER) made +$2.48 on 2026-10-23 and −$18.51 on 2026-10-22. Before entry: opened 0.79× a normal day below yesterday's close on the winning day, opened 2.19× a normal day below yesterday's close on the losing day; yesterday closed at 12% of its range on the winning day, yesterday closed at 97% of its range on the losing day; Friday on the winning day, Thursday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-23 · Breakout: sell US stock (MSFT and AMZN) (learning-only):** Same decision (Breakout: sell US stock (MSFT and AMZN)) made +$6.35 on 2026-10-22 and −$0.38 on 2026-10-23. Before entry: opened right at yesterday's close on the winning day, opened 0.28× a normal day below yesterday's close on the losing day; yesterday's range was 0.78× normal on the winning day, yesterday's range was 1.70× normal on the losing day; yesterday closed at 96% of its range on the winning day, yesterday closed at 23% of its range on the losing day; the trade was against the 50-day trend on the winning day, the trade was with the 50-day trend on the losing day; Thursday on the winning day, Friday on the losing day. After entry: the price went against Roki first on the losing day only; the day's range was 1.2× normal on the winning day and 0.5× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-26 · Breakout: sell BANK NIFTY (learning-only):** Same decision (Breakout: sell BANK NIFTY) made +₹246 on 2026-10-23 and −₹857 on 2026-10-26. Before entry: yesterday's range was 0.95× normal on the winning day, yesterday's range was 1.47× normal on the losing day; yesterday closed at 69% of its range on the winning day, yesterday closed at 33% of its range on the losing day; Friday on the winning day, Monday on the losing day. After entry: the day's move ran against the trade on the losing day only; the price went against Roki first on the losing day only; the day's range was 1.5× normal on the winning day and 0.8× on the losing day. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.
- **2026-10-26 · Breakout: sell HDFCBANK (learning-only):** Same decision (Breakout: sell HDFCBANK) made +₹502 on 2026-10-22 and −₹275 on 2026-10-26. Before entry: opened 0.40× a normal day below yesterday's close on the winning day, opened 0.11× a normal day below yesterday's close on the losing day; yesterday's range was 1.22× normal on the winning day, yesterday's range was 0.67× normal on the losing day; Thursday on the winning day, Monday on the losing day. After entry: the price went against Roki first on the winning day only. Something Roki could see before entering was different, so it goes on the pattern list. One pair proves nothing: the pattern is tested on new trades before any rule change.

## 8. Patterns from those comparisons, tested on new trades only

A pattern is written down the day it is found (in `learning/patterns.json`) and judged only on trades closed after that day, because any idea looks good on the data it came from.

| Rule | Market | When | Found | Then (inside vs rest) | Since (inside vs rest) | Status |
|---|---|---|---|---|---|---|
| (none found yet) | | | | | | |

Rupees and dollars are never added together. Questions: N_H = High breaks, N_L = Low breaks, O_G = Gap fills, O_C = Closes above yesterday's close.
