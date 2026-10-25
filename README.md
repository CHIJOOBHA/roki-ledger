# Roki's public ledger

Proof that what Roki shows in its videos is what Roki actually did. Written only by GitHub Actions
(`.github/workflows/ledger.yml` and `daily-videos.yml` on the main branch); every file has a GitHub commit time.

- `predictions/<session>-gold.json`: gold's night-before calls, locked before the session opened.
- `predictions/<session>-india.sha256` and `.enc`: India's night-before calls, locked before 9:15 am IST as a
  fingerprint only, because SEBI's rule (circular of 8 May 2026) keeps talk of Indian securities to data 30+ days old.
  When the India video covers that day, `predictions/<session>-india.json` is published. Check it matches:
  `sha256sum -c <session>-india.sha256`
- `scorecard.md`: every Sunday, each rule and prediction type against what 5 years of testing said to expect,
  and how the publicly locked calls scored.

Paper trading with real prices. Not investment advice.
