# P-24: Base replaces Sui as Agency Lab's chain

Nov 8, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 8, 2026 |
| Supersedes | P-02 (Sui and Move) |
| Amends | P-03, P-04, P-05, P-07, P-08, P-09, P-14, P-17, P-18 and P-21 |
| Amended by | [P-27](P-27-tempo-second-rail.md) (Tempo as a second measured rail), November 11, 2026 |
| Related | [P-23](P-23-aws-platform.md) (AWS) and [P-25](P-25-agency-lab-name.md) (the name) |

## Summary

**Agency Lab builds on Base, Coinbase's Ethereum layer 2, and its test network, Base Sepolia, because that is where agents' payments carry the most real money and where AWS already settles them.** Contracts are written in Solidity, paid services charge over x402, and everything else stays in Python. Sui stays on the rail-neutral scorecard as one of the rails Agency Lab studies, so the move changes where Agency Lab builds, not what it is willing to say about any chain.

A layer 2 is a blockchain that bundles many transactions and settles them on Ethereum, which makes each one cheap. x402 is the open standard that revives the web's "402 Payment Required" response: a server quotes a price, the agent signs a stablecoin payment and retries, and a facilitator (a service that checks and settles payments) records it on the chain.

## Context

P-02, accepted on November 7, 2026, chose Sui because its base layer settles several steps atomically, holds spending limits as objects and pays gas for beginners. Those strengths are real, but four facts point the build elsewhere.

**Sui's own agent payment rail is not live.** Sui's Agent Payments page says it is "Live on Sui Testnet. Not on Mainnet yet," with paid calls by invitation and no mainnet date. x402 still has no official Sui software kit, which is why P-17 had Agency Lab use Sui's own payment flow instead.

**Base carries most of the dollars.** Counts and dollars point in different directions, so both are reported. In the four weeks from August 22 to September 19, 2026, Solana processed 23.2 million x402 transactions, about 76% of the total, while the XRP Ledger had 3.39 million, Polygon 2.05 million and Base 1.85 million (Solana's figures, built on Artemis data). By value, Base has carried far more over the standard's life: one reading put cumulative x402 volume on Base above $35 million against $7.9 million on Solana. And when Visa's Cuy Sheffield filtered out activity he judged inflated, Base held about 90% of adjusted transactions and 93% of adjusted volume. Since 0.6% to 7.5% of screened x402 commerce looks genuinely agent-driven (TRM Labs), dollars and adjusted counts are the better guide.

**AWS settles on Base.** AgentCore payments, the managed service P-23 adopts, settles x402 in USDC on Base and Solana, and AWS documents funding its wallets with test USDC from Circle's faucet on Base Sepolia.

**Base's funding programs target this exact work.** In July 2026 the Base Ecosystem Fund asked for founders in tokenization, stablecoins, credit and agentic commerce.

## Decision

**Base Sepolia is Agency Lab's only network until an independent audit, and every on-chain part is written in Solidity.** The amended rows follow from that choice.

| Row | Before (Sui) | After (Base) |
| --- | --- | --- |
| P-03 | Test money only on Sui's test network | Test money only on Base Sepolia: test ETH from a faucet and test USDC from Circle's faucet |
| P-04 | One scorecard for every rail, Sui included | One scorecard for every rail, Base included, and the Sector Specialist measures Base, Solana and Sui side by side |
| P-05 | A spending cap the agent holds as a Move object, compared with OpenZeppelin's spend vault for Sui | An allowance the chain enforces through a smart wallet, with a budget, an expiry and an allowed-recipient list; Agency Lab writes its own in Solidity in module 5 and compares it with Coinbase Spend Permissions in module 8 |
| P-07 | Every payment settles in the same transaction as its receipt | Every payment is bound to its receipt: the x402 settlement response, with its transaction hash, is stored with the request, and escrow covers a service that takes the money and fails to deliver |
| P-08 | zkLogin and sponsored transactions; gasless stablecoin transfers | Readers sign in to Coinbase embedded wallets with email or a social login, and their smart accounts' gas is sponsored on Base Sepolia; agents pay with x402's signed USDC authorizations, whose gas the facilitator pays |
| P-09 | Move on-chain, TypeScript for the Sui client, Python for the agent | Solidity on-chain, tested with Foundry; Python for everything else, including the chain client (web3.py), x402 (its Python SDK), the agents (Strands) and the infrastructure (CDK) |
| P-14 | The Move Book and Sui's documentation join the reading list | The Solidity documentation, the Foundry Book and Base's documentation join the reading list; no book or course material goes into Git |
| P-17 | Sui's own payment flow, not x402 | x402 on Base Sepolia through the public testnet facilitator, which needs no API key |
| P-18 | A Sui grant or RFP and Sui's next academic research award | Base's Creator Grant Program for the education track, Base Builder Grants once something ships, and the next Base Batches cohort |
| P-21 | The Sector Specialist analyzes on-chain payments on Sui | The Sector Specialist analyzes on-chain payments on Base first, then Solana and Sui, from the same scorecard |

## Consequences

**Agency Lab gains the most-used rail, a managed payment service, and a far larger body of Solidity tutorials and AI coding help,** which matters because the platform is built by a beginner and written for beginners. Readers keep a gasless first payment: Coinbase's paymaster sponsors smart-account gas on Base Sepolia, and an x402 payment needs no ETH because the facilitator pays the gas.

**Agency Lab loses three Sui features and has to teach around them.** Sui can settle a payment and its receipt in one atomic transaction, while an x402 payment and the service's delivery are separate steps, so module 10's escrow and the statement record carry that guarantee instead. Sui's spending cap is an object the agent holds, while Base's limit lives in a smart wallet's contract, which still makes the chain refuse an overspend. And Google's AP2 partnership with Sui no longer helps, though AP2 itself has an x402 extension and stays a subject of study.

**Coinbase concentration is the main new risk.** Coinbase runs Base's sequencer (the computer that orders its transactions), the wallets, the paymaster and the main facilitator. The scorecard therefore asks of Base exactly what it asks of Sui: who can freeze or reverse a payment, and who can halt the network.

**Funding changes shape.** No program called a "Base Fellowship" was found on November 8, 2026. The Creator Grant Program pays independent creators, educators included, up to $4,000 to produce content about Base. Base Builder Grants are retroactive, for work already shipped. Base Batches puts $100,000 into each of a small number of startups whose primary network is Base; its fall 2026 applications closed on September 9, and its student track was for undergraduates, so the realistic target is a later startup-track cohort.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Stay on Sui with x402 alongside (the November 8 research's first recommendation) | Sui's agent rail is testnet-only and invite-only, x402 has no official Sui kit, and AWS's payment service does not settle on Sui |
| Solana | It led recent x402 counts, but its share swings week to week, it carries far fewer dollars per payment, and Rust is the hardest language here for a beginner |
| Tempo or Arc | Both are new chains built around stablecoin payments, run by permissioned validators, with few grants a student can reach |

## Revisit when

At the rung-3 review; if Base Sepolia loses x402 facilitator or AgentCore payments support; or if Sui's Agent Payments reaches mainnet with an official x402 software kit and Agency Lab's readers ask for it.

## Sources

- Sui, [Agent Payments](https://www.sui.io/agentpayments), on the testnet-only, invite-only status
- CoinStats, [Solana is becoming a key AI payment network](https://coinstats.app/news/c95ad5bc76772e51fdb68fca3e2e1c8ac64bec729b3aa8f58cdaa22e7613d850_Solana-Is-Becoming-a-Key-AI-Payment-Network-A-Bigger-Shift-Is-Unfolding) (September 22, 2026), on the four-week counts by chain
- MEXC News, [Solana briefly overtakes Base in daily x402 transactions](https://www.mexc.com/news/476898), on cumulative x402 counts and volume by chain
- The Defiant, [Visa's Sheffield pegs adjusted x402 volume](https://thedefiant.io/news/infrastructure/visa-s-sheffield-pegs-adjusted-x402-volume-at-19m)
- TRM Labs, [Who's actually paying? Measuring AI agent payments on-chain](https://www.trmlabs.com/trm-tech-blog/whos-actually-paying-measuring-ai-agent-payments-onchain) (September 9, 2026)
- Decrypt, [AWS launches AgentCore Payments with Coinbase and Stripe](https://decrypt.co/?p=367125), on settlement on Base and Solana
- AWS, [Fund an AgentCore payments wallet](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments-fund-wallet.html), on Base Sepolia testnet funding
- Base, [Accepting payments](https://docs.base.org/ai-agents/payments/accepting-payments), on the public testnet facilitator
- Blockscout, [x402 payments](https://docs.blockscout.com/devs/x402-payments), on the x402 Python SDK and gas paid by the facilitator
- Coinbase Developer Platform, [Paymaster](https://docs.cdp.coinbase.com/paymaster/introduction/welcome) and [Embedded wallet smart accounts](https://docs.cdp.coinbase.com/embedded-wallets/evm-features/smart-accounts), on sponsored gas on Base Sepolia
- Coinbase Developer Platform, [Spend Permissions](https://docs.cdp.coinbase.com/wallet-api/v2/evm-features/spend-permissions)
- The Block, [Base is 'permissionless,' says Coinbase's Jesse Pollak](https://www.theblock.co/amp/post/244629/coinbase-base-jesse-pollak), and DEXTools, [Base halts block production after an invalid block](https://www.dextools.io/news/base-coinbase-l2-block-production-halt-sequencer-june-2026) (June 2026), on Coinbase as Base's sole sequencer operator
- Base, [Request for Builders: funding the future of global finance](https://youmind.com/landing/x-viral-articles/base-funding-future-global-finance) (July 16, 2026)
- Granted, [Base Builder Grants](https://grantedai.com/grants/base-batch-accelerator-coinbase-bd563931), a grants directory's summary of the retroactive program
- crypto.news, [Base launches Creator Grant Program](https://crypto.news/base-launches-creator-grant-program-with-up-to-4000-for-creators/)
- Decrypt, [Base narrows its accelerator to 10 startups](https://decrypt.co/375952?amp=1), and Crypto Briefing, [Base Batches 004 applications](https://cryptobriefing.com/base-batches-004-investing-1m-startups/)
- Devfolio, [Base Batches 003 Student Track](https://base-batches-student-track-3.devfolio.co/), on undergraduate eligibility
