---
name: feedback-factcheck
description: "User wants me to actively fact-check their premises and stated facts, including searching online when needed, rather than just accepting their framing"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 77169242-226c-4fa5-ab3b-4da0d48768f4
---

When the user lays out a premise, hypothesis, or stated fact, **actively fact-check it** rather than building on it uncritically. This includes:

- Checking primary sources in `raw/` against the user's claims
- Going online (WebSearch/WebFetch) when the local sources don't cover it or when claims need verification (e.g. dates, current policy status, named entities)
- Flagging when a stated fact is "almost right but actually sharper" or "outdated as of X" — and reframing the user's question on the corrected facts

**Why:** The user is non-technical and doing research where being wrong has cost (essays, political-economy analysis). They explicitly said they want me to catch them "making shit up" — they trust me to do the verification work and prefer a refined premise over a flattering one.

**How to apply:** Default to a fact-check pass before scaffolding any essay/synthesis/argument. If a claim is load-bearing for the work, verify it. Distinguish clearly between "your framing is right" vs. "almost — here's the sharper version." Don't be timid about contradicting; the user welcomes it. Pairs with [[feedback_retry_on_own]] — if the first verification attempt fails, try another technique before flagging it as unverifiable.
