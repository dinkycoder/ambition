# P-26: Agency Lab measures which agent payments come from real agents

Nov 11, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 11, 2026 |
| Supersedes | P-13 (the charter excluded measuring fake or wash agent activity) |
| Related | [P-24](P-24-base-chain.md) (Base), [P-27](P-27-tempo-second-rail.md) (Tempo) and [P-28](P-28-micro-research-and-education-platform.md) (the platform's description) |

## Summary

**Agency Lab now measures how much agent-payment traffic comes from genuine AI agents rather than scripts, tests or wash trading, because that measurement is the most valuable data in the field and no one publishes a method others can check.** Every headline figure for agent payments is inflated by traffic that only looks like agents paying, so a builder, a payment company or a regulator who reads raw counts reads mostly noise. The Sector Specialist publishes a Genuineness Estimate each quarter: the share of x402 and MPP payments that look genuine, as a range with a confidence band, under a versioned method published in full.

Two limits keep the work safe. The desk publishes only totals and shares, never a public verdict that a named address, agent or business is fake, and it reads public ledgers without ever sending a real-money transaction.

## Context

P-13, accepted on November 7, 2026, kept this work out for three reasons: it needed data access Agency Lab wouldn't have, it needed legal review, and it would turn a teaching desk into a policing one. Each reason now has an answer.

**The data is public.** Every x402 payment on Base and every MPP charge on Tempo settles on a public ledger, so reading it costs nothing and needs no one's permission. Dune's curated agentic-payments dataset already covers x402 and MPP's on-chain Tempo payments in one table.

**Publishing totals avoids the legal risk.** Calling a named address or business fake invites claims of defamation and interference with its business, while a share computed over all traffic accuses no one. TRM Labs and Visa with Artemis publish exactly this kind of total. Agency Lab follows that practice and adds what they leave out: a method anyone can rerun.

**A measurement is research, not policing.** The desk reports what share of traffic looks genuine and how sure it is, the same way an economist estimates unemployment without naming who is out of work.

**The gap is real.** TRM Labs judged only 0.6% to 7.5% of $25.62 million of screened x402 commerce to come from real agents (September 9, 2026), a range more than twelve times wide, and it notes that nothing in the protocol requires an agent, so a scheduled script and an agent can leave the same record. Visa and Artemis cut $135.7 million of raw x402 volume to $15.0 million (July 2026) with heuristics they have not published. Three reputable studies count the same protocol differently, and none can be rerun by an outsider.

**The founder's background fits the problem.** Telling genuine agents from scripts is a judgment made from behavioral signatures under uncertainty, which is the daily work of intelligence analysis and sanctions screening. That work brings habits the current studies lack: graded sources, stated confidence and a written method that a second analyst can check.

## Decision

**The Sector Specialist owns the Genuineness Estimate, and it follows six rules.**

1. **Totals only in public.** Briefs report shares and counts over all traffic or over named segments, such as a facilitator or a price band, never a verdict on an identifiable address, agent or business. The Compliance Agent fails any brief that does (rule R17).
2. **A range, not a point.** Each estimate gives a permissive and a strict share, in the style of TRM's two tests, with a confidence band and estimative words ("likely", "almost certainly") defined in the glossary.
3. **A published, versioned method.** The signals, thresholds and code version that produced an estimate are published with it, and a method change takes a new version number and a rerun of the previous quarter, so a change in the estimate can be told apart from a change in the method.
4. **Labeled examples from known sources.** The desk's own instrumented agents produce payments known to be genuine, and a deliberately simple scripted bot produces payments known to be scripted, both on test networks. These labels calibrate the method; because testnet behavior only approximates mainnet, the published shares come from mainnet signals, and the labels never stand in for them.
5. **Read, never send.** The desk reads Base and Tempo mainnet ledgers through public endpoints and data warehouses, and it never sends a mainnet transaction. P-03's test-money rule is unchanged, because reading moves no money.
6. **The desk's own traffic stays out of the market figures.** Its addresses are listed and excluded from every mainnet estimate, and its testnet payments appear only as labeled examples.

The signals start from what the published studies use, such as how long an address stays active, how many separate sellers it pays, whether it is registered under ERC-8004, how regular its timing is and whether its funds go round in a loop, and the method records which ones each version uses.

## Consequences

**The register gains its most valuable output and its most sensitive one.** The estimate gives readers and paying agents a number they cannot get elsewhere, and it gives the education track a lesson in reading evidence that is mostly noise. It also creates the one output that could hurt a named party if it leaked into a brief, so the public-totals rule is enforced in code and by the Compliance judge, not left to the writer.

**The Director's scope changes.** "What share of x402 payments come from genuine agents?" is now in scope, while "Is this address a wash trader?" still ends before any money is spent.

**Earlier text changes.** The Sector Specialist's rule "a disclosure, never a score" becomes the six rules above. The Micro Economist no longer declines an unfiltered agent transaction count; it reports one only beside the genuineness-adjusted estimate and its method.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep P-13 | The field's headline numbers would stay unchecked, and the desk would give up the data that makes its research worth paying for |
| Publish address-level scores | A public verdict on a named party carries legal risk and could harm an honest builder wrongly flagged |
| Rely on TRM's or Artemis's figures | Their ranges are wide or their methods unpublished, so the desk could not explain a change in its own briefs |

## Revisit when

At the rung-5 gate, or before any output names an address, agent or business, which needs a written legal review first.

## Sources

- TRM Labs, [Who's actually paying? Measuring AI agent payments on-chain](https://www.trmlabs.com/trm-tech-blog/whos-actually-paying-measuring-ai-agent-payments-onchain) (September 9, 2026)
- Visa, [Agentic payments report](https://www.visa.com/api/image-proxy?path=%2Fcontent%2Fdam%2Fvisa%2Freimagine-visa%2Fthought-leadership%2Fdocuments%2Fagentic-payments-report.pdf) (July 2026), with Artemis data to April 21, 2026
- Four Pillars, [x402 on Polygon: real or gamed?](https://research.4pillars.io/en/research/x402-on-polygon-real-or-gamed)
- Allium, [Visa x Allium: making sense of stablecoins](https://allium.so/blog/visa-x-allium-making-sense-of-stablecoins/)
- Dune, [Agentic payments curated dataset](https://docs.dune.com/data-catalog/curated/payments/agentic-payments.md), covering x402 and MPP's on-chain Tempo payments
- Token Terminal, [Agentic payments explorer](https://tokenterminal.com/explorer/agentic-payments)
- Notabene, [Know your agent: KYA in agentic payments](https://notabene.id/post/know-your-agent-kya-agentic-payments), on why an agent choosing the payee doesn't remove sanctions liability
