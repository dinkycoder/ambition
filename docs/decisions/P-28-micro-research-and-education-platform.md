# P-28: Agency Lab is a Micro Research and Education Platform

Nov 11, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 11, 2026 |
| Amends | P-01 (the case study) and P-21 (the committee's economist) |
| Related | [P-25](P-25-agency-lab-name.md) (the name, unchanged) and [P-26](P-26-measure-agent-genuineness.md) (the Genuineness Estimate) |

## Summary

**Agency Lab describes itself as a Micro Research and Education Platform (MREP), because what it studies is agents paying agents in tiny amounts, and the economics of the markets those payments create.** *Building the Agentic Enterprise* runs its whole case study on a fictional Macro Research and Education Platform with the same acronym (Preface, p. xxxii). Keeping the acronym and changing one word keeps the mapping to the book's chapters easy to follow, while saying plainly how Agency Lab differs.

Agency Lab stays the name (P-25). MREP is the description of what it is, the way "a lab" or "a newsletter" describes a brand.

## Context

**"Micro" is accurate twice over.** It names the payments: more than 87% of the x402 payments on Base that Chainalysis sampled were worth between $0.0001 and $0.10, with one to ten cents the most common size (October 2026), the size of an agent buying one answer or one page from another agent, where consumer checkout runs to tens or hundreds of dollars. It also names the economics: the committee's economist asks how agent markets set prices, whether agents sharing a model raise markups and whether platforms capture the surplus, which are microeconomic questions about individual markets rather than whole economies.

**"Micro" describes the style, not a size limit.** Chainalysis also found that payments of $1 or more carried about 95% of the value moving through x402 on Base by early 2026, up from 49% in early 2025, so the desk keeps measuring larger agent payments, and the Genuineness Estimate reports by price band.

**The shared acronym needs care.** A reader who knows the book will meet "MREP" there as the Macro platform and here as the Micro one.

## Decision

**Every current document calls Agency Lab a Micro Research and Education Platform at first use, spelled out in full, and uses "MREP" alone only after that.**

| Item | Before | After |
| --- | --- | --- |
| P-01 | An agentic commerce research and education platform | A Micro Research and Education Platform (MREP) for agentic commerce, with the same three parts |
| P-21 | The Macro Economist (the book's economist, retooled) | The Micro Economist (the book's Macro Economist, retooled for agent markets); the stablecoin and Treasury-bill link stays as background |
| References to the book's case study | "The book's MREP" | "The book's Macro Research and Education Platform", so the acronym always means Agency Lab in this repository |
| Name and mission | Agency Lab; "Help AI builders give their agents money safely, one small win at a time." | Unchanged |

## Consequences

**The description now matches the work.** P-26 makes measuring agent micropayments the desk's main output, and P-27 adds the second standard built for them, so a description naming the scale of those payments tells a reader what the platform does before they open a brief.

**The book stays a source of disciplines, not a template for the subject.** Its macro desk studies economies, while Agency Lab studies agent markets, so the change also marks where the case study ends and Agency Lab begins.

## Alternatives considered

| Option | Why not |
| --- | --- |
| No description, "Agency Lab" alone | Readers would have to open a document to learn what the platform studies |
| "Agentic Commerce Research and Education Platform" | Accurate but long, and it drops the link to the book's chapters that the shared acronym keeps |

## Revisit when

If larger agent payments, such as consumer checkout through ACP or AP2, become most of what the desk measures.

## Sources

- Jaroslav Pantsjoha, [*Building the Agentic Enterprise*](https://www.oreilly.com/library/view/building-the-agentic/9781807604455/) (Packt, September 2026), Preface, p. xxxii, cited by page with no quotation
- Chainalysis, [x402 agentic payments adoption](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/), on the share of value above $1, as reported by [Cointelegraph](https://cointelegraph.com/news/agentic-payment-activity-surpasses-100m-transactions-on-base) (June 2026)
- Blockhead, [AI agents have made 138 million payments over x402, most of them under 10 cents](https://www.blockhead.co/2026/10/15/ai-agents-have-made-138-million-payments-over-x402-most-of-them-under-10-cents/) (October 15, 2026), reporting the North America chapter of Chainalysis' 2026 Geography of Cryptocurrency Report
