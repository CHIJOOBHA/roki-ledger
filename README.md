# Roki's public record

Roki is an AI learning to trade in public, with paper money, real prices and real costs. This repository is its
record. Every file is written by GitHub Actions only, and each commit's time stamp shows when it was written, so
nothing here can be changed after the fact without it showing in the history.

Read it as a page: **https://confluenceengine.vercel.app/public**

| Folder or file | What it is |
|---|---|
| `predictions/<day>-india.json`, `-gold.json` | The night-before calls, locked before the market opened |
| `redteam/<day>-<group>.json` | The red team's warnings against those calls, locked at the same time |
| `reports/<day>.md` | Every trade of the session: why Roki took it, what happened, why it won or lost, the lesson |
| `prices/<day>.json` | The session's prices checked against a second series and official sources (NSE, Coinbase) |
| `scorecard.md`, `twin.md` | Weekly: every rule and prediction against its testing, and Roki against its never-learning twin |
| `learning/` | Patterns Roki is testing on new trades, and every change it made to itself |
| `rules-changes.md` | Every recorded change to Roki's rules |

The engine that produces this is private. The record shows every decision and its result, not the rules' exact numbers.

Paper trading with real prices. Not investment advice.
