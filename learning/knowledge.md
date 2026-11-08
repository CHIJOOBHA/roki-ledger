# What Roki knows

Each concept: what it is, why traders care, and how Roki uses it today. "Measured" means Roki reads it from real
prices every day and its rules or research can use it. The weekly AI analyst reads this page too, so its ideas use
the same meanings. Ideas built on any of these are only trusted after Roki's 5-year test and a live trial.

## Price and the day

| Concept | What it is | Why it matters | How Roki uses it |
|---|---|---|---|
| Yesterday's high, low, open, close | The previous session's four prices | Where buyers and sellers last fought; levels many traders watch | Core of every rule and prediction (measured) |
| Normal day's move (ADR) | Average high-to-low range of the last 10 sessions | Puts every move in proportion: 100 points is big for one market, tiny for another | Gaps, stops and moves are all measured in it (measured) |
| Gap | Open minus yesterday's close | Overnight news; big gaps often partly fill, small ones in US indices tend to run | Gap-fade rules; "small gap and go" trial in US indices (measured) |
| Where yesterday closed (CLV) | Close's position in the day's range, 0 to 1 | A close at the extreme shows who won the day; extremes often reverse next day | Extreme-close fade rule (measured) |
| Inside day, NR7 | A day inside the one before; the narrowest of 7 days | Quiet days store energy; ranges tend to expand afterwards | Self-research ideas (measured) |
| Candle body | Close minus open, as a share of the range | Conviction: open-at-low, close-at-high days show strong buyers | Self-research ideas (measured) |
| Breakout / breakdown | Price crossing yesterday's high or low | Trend traders buy breaks; range traders fade them. Which wins depends on the market | Breakout rule (retired in crypto after losing live); fade-the-break ideas (measured) |

## Trend, momentum and mean reversion

| Concept | What it is | Why it matters | How Roki uses it |
|---|---|---|---|
| 50-day average and trend | Average close of 50 sessions; above it = uptrend | Big funds follow trends; trades with the trend tend to last | Big-gap rule and research (measured) |
| Momentum | Recent winners keep winning for a while | Works over weeks and months, rarely within one day | 5-day move measured; multi-day holding not yet built |
| Mean reversion | Stretched prices snap back | Works over hours and days in index markets | Gap fades, oversold/overbought and stretched-from-average ideas (measured) |
| Volatility regime | Quiet, normal or wild markets | Rules that work in quiet markets often fail in wild ones | Volatility ratio and skip days (measured) |

## The wider market (macro)

| Concept | What it is | Why it matters | How Roki uses it |
|---|---|---|---|
| India VIX | Expected Nifty volatility over 30 days, from option prices: the fear gauge | High VIX = big, emotional moves; spikes often mark short-term bottoms | Self-research ideas (measured) |
| US VIX | The same for the S&P 500 | Global fear; very high VIX often precedes rebounds | Self-research ideas (measured) |
| Overnight US move | The S&P 500's last day | India often follows the US at the open | Night-before predictions and research (measured) |
| Dollar-rupee | Price of a dollar in rupees | A falling rupee often means foreign investors are selling Indian shares | Self-research ideas (measured) |
| Crude oil | Brent/WTI price | India imports most of its oil: costly oil hurts the rupee, inflation and Indian markets | Self-research ideas (measured) |
| FII / DII flows | Daily buying and selling by foreign and domestic institutions | Big foreign selling moves Indian markets for days | Not yet: NSE publishes it, but Roki can't download it from here |
| Events | RBI policy, US Fed, US CPI, the Union Budget, results, expiry days | Volatility jumps; normal patterns often break | Expiry days tested (no edge found); an event calendar is not built yet |

## Options

| Concept | What it is | Why it matters | How Roki uses it |
|---|---|---|---|
| Call / put | Right to buy / sell at a set price before expiry | Small premium, big leverage | Roki buys the at-the-money call or put for counted Indian trades (paper) |
| Premium and time decay (theta) | An option loses value every day it isn't moving | Buyers need the move to come quickly; sellers earn the decay | Buying only today; this is why option buying turned a small index edge into losses |
| Implied volatility (IV) | The volatility priced into options | High IV = expensive options; selling is paid more | Modelled from VIX in the paper account; not traded on |
| Open interest, put/call ratio | Open contracts at each strike | Shows where large players are positioned | Not yet: needs NSE option-chain data |
| Option selling with a hedge (spreads) | Sell an option, buy a further one to cap the loss | How most professional option income is made | Not yet built (planned, paper only) |

## Risk and money

| Concept | What it is | Why it matters | How Roki uses it |
|---|---|---|---|
| Costs | Brokerage, STT, exchange fees, stamp duty, GST, slippage | A small edge disappears after costs | Every result is after real costs (measured) |
| Stop-loss | A planned exit when wrong | Caps the loss of one trade | 1 normal day's move on every trade |
| Daily loss limit | Stop trading after a bad day | Prevents one bad day becoming a disaster | Portfolio risk desk: no new counted trades after -2% across markets |
| Correlation | Markets that move together | Three Indian index buys are really one bet | At most 3 counted same-direction trades per market group a day |
| Position sizing | How much to put on each trade | The same idea can win or ruin depending on size | Each trade is sized so its safety stop loses about 1% of its paper size: bigger in calm markets, smaller in wild ones |
| Drawdown | Fall from the best point | What investors feel; decides if a system survives | Brake: half size from 5% below the best point, counted trading paused from 10% until it recovers |
| Overfitting and luck | A rule that fit the past by chance | Most backtested "edges" are luck | Two-half test, minimum 40 trades, strict t-statistics, a luck check across all tests (Benjamini-Hochberg), live trial before counting |
