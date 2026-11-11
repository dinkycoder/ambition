# P-27: Tempo and MPP become Agency Lab's second measured rail

Nov 11, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 11, 2026 |
| Amends | P-04 (rails measured side by side), P-21 (the Sector Specialist's reading order) and P-24 (Base as the chain) |
| Related | [P-24](P-24-base-chain.md) (Base) and [P-26](P-26-measure-agent-genuineness.md) (the Genuineness Estimate) |

## Summary

**Agency Lab keeps building on Base, and it adds Tempo, with the Machine Payments Protocol (MPP), as the second rail it measures and teaches, because the field now has two agent-payment standards and a referee that watches only one cannot call itself neutral.** Tempo is a blockchain built for stablecoin payments by Stripe and Paradigm, and MPP is the payment standard Stripe and Tempo wrote for it. Like x402, MPP lets a server answer a request with "402 Payment Required" and lets an agent pay and retry.

Base stays the build chain because x402 on Base still carries far more money and records each payment on the chain, which is what the Genuineness Estimate needs. A clear trigger reopens that choice if MPP overtakes it.

## Context

**Tempo is a serious second rail.** It launched its mainnet on March 18, 2026 alongside MPP, after raising $500 million at a $5 billion valuation in October 2025. It has no gas token of its own, so fees are paid in stablecoins, and its documentation cites finality of about half a second. Its validators began as a permissioned set, with Stripe, Visa and Zodia Custody added as the first outside validators in April 2026.

**AWS and Python already reach it.** AgentCore payments orchestrates both x402 and MPP, and Stripe announced on August 18, 2026 that AgentCore payments supports MPP through Privy wallets. Tempo maintains `pympp`, a Python SDK for MPP, and runs a test network, Tempo Moderato. MPP is also built to work across rails: its TypeScript client can pay x402-compatible endpoints as well as native MPP ones, so one agent can work with both standards.

**The money is still on x402.** Merit Systems' MPPScan counted about $314,000 of total MPP volume on November 11, 2026, while x402's lifetime totals run from about $42 million to $53 million across the studies in P-26.

**MPP's cheapest mode hides most of what the estimate measures.** In an MPP session the agent deposits funds, signs off-chain vouchers for each request and settles at the end, so only the opening and closing reach the chain. The request-by-request rhythm that separates an agent from a script mostly stays off the ledger. One-time MPP charges do settle on the chain, and Dune's dataset tracks both kinds on Tempo.

## Decision

**Base remains the only network Agency Lab builds on, and Tempo joins as the second rail it measures and teaches.**

| Row | Before | After |
| --- | --- | --- |
| P-04 | Base, Solana and Sui measured side by side | Base, Tempo, Solana and Sui measured side by side, and x402 and MPP compared in the same briefs |
| P-21 | The Sector Specialist reads Base first, then Solana and Sui | The Sector Specialist reads Base first, then Tempo, then Solana and Sui |
| P-24 | Tempo was set aside as a new chain run by permissioned validators | Base stays the build chain; Tempo is scored and measured, and a quarter in which MPP's on-chain value tops x402's on Base reopens P-24 |

**Three things follow.** Tempo answers the same eight scorecard questions as every other rail. The Genuineness Estimate covers x402 and MPP, and it reports MPP sessions as a named blind spot rather than guessing at their off-chain traffic. And an MPP payment on Tempo Moderato joins the curriculum only as an optional lesson after rung 3, once AWS's documentation confirms that AgentCore payments can fund a wallet on Tempo's test network.

## Consequences

**The desk becomes the place where the two standards are compared on the same questions,** which is the neutral position P-04 promises and the one a buyer of research would pay for.

**The curriculum stays the same size.** Modules 1 to 12 are unchanged, because the build stays on Base and AgentCore's single payment call already handles both protocols.

**Stripe concentration joins Coinbase concentration on the scorecard.** Stripe co-wrote MPP, helps run Tempo's validators and owns Privy, much as Coinbase runs Base's sequencer and its main facilitator, so question 5, about who can freeze, reverse or halt a payment, is asked of both.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Move the build to Tempo | MPP carries a small fraction of x402's money, and its sessions keep most of the per-request signal off the chain |
| Leave Tempo out | The desk would measure one of the two standards and could not claim to be neutral |

## Revisit when

At the rung-3 review, or after any full quarter in which MPP's on-chain value exceeds x402's on Base.

## Sources

- The Block, [Tempo mainnet goes live with Machine Payments Protocol for agents](https://www.theblock.co/amp/post/394131/tempo-mainnet-goes-live-with-machine-payments-protocol-for-agents) (March 18, 2026), on the launch and the $500 million round
- Tempo, [Mainnet](https://tempo.xyz/blog/mainnet), on MPP as an open, rail-agnostic standard, and [Make agentic payments with MPP](https://docs.tempo.xyz/docs/guide/machine-payments), on finality, fees and the Python SDK
- Tempo, [MPP Sessions](https://agents.tempo.xyz/blog/mpp-sessions), on sessions and the Tempo Moderato test network, and [Tempo docs index](https://docs.tempo.xyz/wallet), on off-chain vouchers
- Everstake, [What is Tempo?](https://everstake.one/resources/blog/what-is-tempo-stripe-and-paradigms-stablecoin-payments-blockchain-explained) (July 22, 2026), on stablecoin fees and the first outside validators
- AWS, [Process a payment with AgentCore payments](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments-process-payment.html) and [AgentCore payments](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments.html), on x402 and MPP
- CreateWith, [Stripe adds MPP for Amazon Bedrock AgentCore](https://www.createwith.com/tool/stripe/updates/stripe-adds-machine-payments-protocol-mpp-for-amazon-bedrock-agentcore-support), a secondary summary of Stripe's August 18, 2026 announcement
- MPP, [Python SDK](https://mpp.dev/sdk/python) and [mppx agent runtimes](https://mpp.dev/blog/mppx-agent-runtimes), on `pympp` and paying x402-compatible endpoints
- Merit Systems, [What is MPP?](https://www.merit.systems/glossary/what-is-mpp), on MPPScan totals, read November 11, 2026
- Dune, [Agentic payments curated dataset](https://docs.dune.com/data-catalog/curated/payments/agentic-payments.md)
