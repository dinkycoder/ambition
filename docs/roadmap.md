# Agency Lab Roadmap and Decision Register

Nov 8, 2026 · @dinky

## Summary

**Agency Lab is an agentic commerce research and education platform on AWS and Base, with stablecoins at its center.** AI agents will pay for things in digital dollars, so Agency Lab teaches builders how an agent holds and spends stablecoins safely. It also scores every payment rail and stablecoin on one public scorecard, and ships the toolkit that does the spending.

The platform has three parts that feed each other. The toolkit gives an agent a wallet, a spending allowance it cannot exceed, payments bound to their receipts, escrow and alerts. The research desk uses that toolkit to buy data and publish cited briefs on which rails and stablecoins are safe for agents. The education track turns each module into a lesson and a reader challenge that leaves public proof on Base Sepolia, Base's free test network.

Base carries the build because that is where agents' payments carry the most money and where AWS already settles them (P-24). AWS runs the agents, keys and records because its managed services pay for things on Base natively, and because the book's disciplines never depended on Google's services (P-23). The research stays neutral anyway, because a referee that favors its own rail would lose the trust that makes its briefs worth buying.

**P-01 to P-22 were accepted on November 7, 2026, and P-23 to P-25 on November 8, 2026.** P-23 moves the platform from Google Cloud to AWS, P-24 moves the chain from Sui to Base, and P-25 renames Ambition to Agency Lab; each has its own decision record in [docs/decisions](decisions/). The Sui and Google Cloud roadmap is kept unchanged as a [dated record](archive/roadmap-sui-google-cloud-2026-11-07.md), as is the earlier [Base and Solidity roadmap](archive/agentic-enterprise-roadmap-2026-11-04.md) with its decisions D-01 to D-26. The plan stays dateless, and dates return when the capstone course begins (P-15).

## Why this platform

**Starting from a blank page, three ambitious DeFi paths on Base were weighed, and only the platform is both ambitious and reachable for one builder.** The other two need licenses or capital that a student project cannot raise, and Base's largest players already hold them.

| Path | Verdict | Why |
| --- | --- | --- |
| Issue a stablecoin | No | Under the GENIUS Act, only a regulated "permitted payment stablecoin issuer" may issue one to people in the US, and the law is expected to take effect January 18, 2027. Base already runs on Circle's USDC, which most x402 payments use |
| Build a trading, lending or derivatives protocol | No | Base already has Aerodrome's exchange and Morpho's lending markets. The May 2025 Cetus exploit on Sui showed that one math bug in an exchange can drain over $220 million, so a new protocol needs deep capital and repeated audits |
| Build an agentic commerce research and education platform | Yes | It sits one layer above the stablecoins, so it needs no license to issue and no pool of other people's money. It uses exactly the Base features that make agent payments practical, and a neutral scorecard of rails and stablecoins is something no one offers today |

The stablecoin angle survives inside the winning path. Agency Lab studies, teaches and uses stablecoins rather than issuing one, which keeps the ambition while staying outside the issuer rules. This is a summary of public reporting, not legal advice.

## The case study

**The case study is Agency Lab itself, growing from one agent with a wallet into a governed desk that other builders' agents pay for research.** It replaces the book's fictional macro-research firm with a real subject, agents paying in stablecoins, so every lesson Agency Lab teaches is also a part it runs.

| Part | What it does | The Base and AWS features it uses |
| --- | --- | --- |
| Toolkit | Gives an agent a wallet whose key never leaves AWS KMS, a spending allowance a smart wallet enforces, payments bound to their receipts, escrow with automatic refunds, alerts and statements | Smart-wallet allowances, x402 payments in USDC whose gas the facilitator pays, AWS KMS signing with a secp256k1 key, and AgentCore payments as the managed comparison |
| Research desk | Buys public data with the toolkit and publishes cited briefs that score each rail and stablecoin on the same scorecard. It covers risk, safety and how-to, never price calls or personal recommendations | The toolkit's own x402 payments, so every brief is also a live test; S3 for the cited library; paid briefs sold over x402 |
| Education | Turns each module into a plain-language lesson and a reader challenge that leaves public proof on Base Sepolia | Coinbase embedded wallets, so a beginner signs in with email or a social login, and sponsored smart-account gas, so a reader's first payment needs no test ETH |

The three parts feed each other. A reader learns a module, the toolkit gains a tested part, and the desk spends through that part to produce research. When the desk buys from several services for one brief, each purchase is a separate x402 payment, so escrow protects the ones that matter most.

## The ladder

**Five rungs take Agency Lab from one agent with a wallet to a desk that other agents pay for research, and each rung closes on a gate anyone can check.** A missed gate holds the next rung rather than lowering the bar.

![Each rung closes on a gate, from one agent to a paid research desk](img/roadmap-ladder.png)

Rungs 1 to 3 hold the twelve modules. Rung 5 is the platform's destination rather than one option among several, because the research and education desk is the case study.

## Modules 1 to 12 in Solidity and Python

**Every module ships working code on Base Sepolia as well as a lesson, and each one is done when its check passes.** Solidity is used only for code that runs on the chain, and everything else is Python. AWS joins in module 1 with a small foundation and adds one service at a time.

| Module | What it builds on Base | Reader challenge | What runs on AWS |
| --- | --- | --- | --- |
| 1 | An agent wallet whose key is created in AWS KMS, and a Python script that reads its transactions | Get test ETH from a Base Sepolia faucet, send some to yourself and reply with the block-explorer link | Account guardrails: a protected root login, a day-to-day admin login and an AWS Budgets alarm. The agent's secp256k1 key in KMS, and a first Lambda that CDK deploys from GitHub Actions through OIDC, writing the first release manifest |
| 2 | A statement: a script that turns the agent's activity into a readable record and explains blocks, transaction hashes and finality | Find the block that holds your transaction and reply with its number | An indexer Lambda reads the agent's transactions block by block and writes the statement index to DynamoDB |
| 3 | A first Solidity contract, tested with Foundry: a shared registry where agents list a name and a price per request | Add an entry; each one is public proof | A separate KMS deployer key, usable only by the GitHub deploy role, signs the deployment, and the CDK stack gains its first tests |
| 4 | Test USDC from Circle's faucet and a payment from the agent to another wallet | Send 1 test USDC between two of your own wallets and reply with the link | The pay Lambda signs with KMS behind a first write-back gate that fails closed, and EventBridge Scheduler starts each run |
| 5 | A spending allowance enforced by a smart wallet, with a budget, an expiry and an allowed-recipient list that the owner can suspend or revoke | Grant, then revoke, an allowance and reply with the revocation | The gate checks the allowance before signing, refused attempts go to the near-miss log, and the kill-switch runbook names its steps |
| 6 | A paid service that charges per request over x402, and an agent that pays it and stores the receipt with its request | Pay the service once and reply with the settlement transaction | The service runs on API Gateway and Lambda with x402's Python middleware; the agent's loop runs in Strands Agents on Bedrock with a traffic-class tag and a per-run ceiling; the test set starts with 20 cases |
| 7 | Gasless payments: the agent pays with x402's signed USDC authorization, and a new reader pays from an embedded-wallet smart account whose gas is sponsored | Make a first payment from a sponsored smart account and reply with the link | No new service; the paymaster's spending limit is set in Coinbase's portal and recorded in the release manifest |
| 8 | Tests, a security checklist and a first kill-switch drill; module 5's allowance is compared with Coinbase Spend Permissions | Try to overspend a test allowance and reply with the failed transaction | An IAM review, the OWASP agentic-risk mapping, a first Well-Architected review and the first dated drill |
| 9 | Agent version 1: buys data over x402, stays under its allowance and logs every payment and refusal, then repeats the task through AgentCore payments | Call the paid service from your own code | AgentCore Runtime hosts the agent and AgentCore payments runs the managed path under a session budget; X-Ray traces every run, and the spending audit comes from CloudWatch Logs Insights and Athena |
| 10 | Escrow: a contract that holds a payment until delivery and refunds it after a deadline | Pay into escrow, let the deadline pass and reply with your refund | The deadline lives in the contract, and a one-time EventBridge Scheduler schedule claims the refund once it passes |
| 11 | Alerts and a public spending page | Trip an alert on your practice wallet and reply with the link | DynamoDB Streams trigger an alert Lambda that emails through SNS, and CloudFront serves the page from a private S3 bucket |
| 12 | Agency Lab version 1, a capstone-style write-up and the first published scorecard brief | Read the brief and score one rail or stablecoin yourself | The Sector Specialist runs on AgentCore Runtime; the architecture diagram, the Well-Architected review, a cost report from Cost Explorer and the rung-3 gate review |

The research desk starts small inside module 12 rather than waiting for a later rung. That way the first scorecard is tested by readers before the desk grows into the multi-agent research operation in rung 5. **Readers never need an AWS account,** because every challenge happens on Base Sepolia.

## The rail-neutral scorecard

**Every chain and every stablecoin answers the same eight questions, Base and its dollars included (P-04).** The first four come from the Sui Foundation's post on agentic commerce and test whether a rail can carry agent payments. The four Agency Lab adds test whether a builder can trust it, which is the part a vendor's checklist leaves out.

| Question | Asked of | Why it matters to an agent |
| --- | --- | --- |
| Can one workflow settle atomically across several services? | Rails | An agent that pays but never receives what it bought has lost money it cannot reverse |
| Can the protocol enforce a spending limit that travels across apps? | Rails | A limit that each app enforces separately fails the first time an app forgets |
| Do cost and throughput hold when one account drives thousands of payments? | Rails | Agents pay per request, so fees that look small per payment add up |
| Can the agent pay in stablecoins without managing gas? | Rails | An agent that must also hold the chain's own token has two balances to run out of |
| Can anyone, validators, sequencers or issuers included, freeze, reverse or halt a payment? | Rails and stablecoins | Sui's validators froze about $160 million after the Cetus exploit, issuers can freeze their own coins, and a layer 2's sequencer decides what gets in, so builders should know who holds that power |
| Can a buyer get a refund when a service fails to deliver? | Rails | Payments are final, so refunds must be built in, usually as escrow |
| Can a reviewer trace why money moved? | Rails | An audit trail is what lets a team lead trust an agent with a budget |
| What backs the dollar, and who can redeem it? | Stablecoins | USDC holds cash and short-term Treasury reserves that Circle has examined monthly, while a synthetic dollar such as Ethena's USDe is hedged with short futures, so each can fail in a different way |

Each brief scores one rail or stablecoin against these questions, cites a source for every answer, and says "insufficient evidence" where the sources run out. Base gets no easier questions for being Agency Lab's home.

## Six safety habits

**Six habits from *Building the Agentic Enterprise* carry over unchanged, because none of them depended on the chain or the cloud (P-10).** Each starts small in an early module, since every one is cheap to begin and expensive to bolt on later.

| Habit | What Agency Lab does | Starts in | Book |
| --- | --- | --- | --- |
| Release manifest | Every deploy writes one file naming the model tier and ID, prompt hashes, tool and library versions, contract addresses and allowances, and every statement line names the manifest it ran under | Module 1 | pp. 421–425 |
| Write-back gate that fails closed | Nothing the agent proposes reaches the signer until the gate passes it, and an error, a timeout or a missing record counts as no (P-06) | Module 4, complete in module 5 | pp. 303–304, 692 |
| Kill switch with named steps | The runbook names each step: revoke the allowance, pause the schedules, deny the agents' IAM roles and add an AgentCore Policy rule that denies every payment tool, and the same flag stops API Gateway (P-22). A drill at every rung gate from rung 2 on, dated in the log, proves it still stops a test agent within a minute | Module 5, first drill in module 8 | pp. 524, 707 |
| Test-set gate | The test set holds at least 20 cases from module 6. From rung 5, a 50-query smoke set runs on every commit, and the golden set of 200 or more queries runs only when a unit joins and at each rung gate, on Bedrock batch inference, against one pass bar of 0.90; overspending, a wrong recipient or a leaked key must pass 100% | Module 6 | pp. 605, 705 |
| Near-miss log | Every payment the gate refused or sent for approval is logged with its reason, because a near miss is the cheapest warning a system gives | Module 5 | p. 467 |
| Cost tags and a per-run ceiling | Every model call carries a traffic-class tag, such as agent run, test set or reader service. At 90% of a run's ceiling the agent switches to a cheaper model, and at 100% the run stops | Module 6 | pp. 411, 518 |

**Two candidate habits come from the agentic-economy papers. Neither is accepted, and the register below does not include them.** The first is an agent-trap test: a web page or document that tells an agent to spend or approve must fail closed, and the case joins the starter set (Tomasev et al., 2025, arXiv:2509.10147, on agent traps). The second is credit logging: every finding records the agent, snapshot and hash that produced it (Tomasev et al., 2025, on tracing value back through agent chains). Both add to the test set and the near-miss log, so they would take effect only after you accept them.

## The architecture on AWS and Base

**Every payment passes a gate in code, a signature inside AWS KMS and the smart wallet's own limit on Base before it settles.** AWS runs the agents, their keys and their records, while Base holds the money and the rules that must never be edited (P-11, P-23, P-24).

![Every payment passes the gate, the KMS signer and the smart wallet's allowance before it settles on Base](img/architecture.png)

The agent can propose any payment, but only the gate can pass one to the signer, only the signer holds the key, and the smart wallet refuses anything over its allowance. Everything off the chain is Python, and contracts are Solidity (P-09).

**A second, managed path runs beside the first from module 9.** AgentCore payments signs through a Coinbase CDP or Stripe Privy wallet whose key that provider holds, and it caps each payment session with a budget and an expiry. Agency Lab teaches both paths, publishes how they compare on the same task, and lets the research desk use whichever passes its gate cases (P-06).

**The design answers each of AWS's six Well-Architected pillars with a named control, and the rung-3 review checks them again.**

| Pillar | Agency Lab's answer |
| --- | --- |
| Operational excellence | Only GitHub Actions deploys, through the CDK stack; every deploy writes a release manifest, every run writes a structured log and trace, and the kill switch is drilled at every rung gate from rung 2 on |
| Security | One least-privilege IAM role per function and agent, a wallet key that signs only inside KMS for a smart wallet that enforces its own limit, AgentCore Policy on every payment tool, OIDC instead of stored keys, and a protected root login |
| Reliability | Lambda and DynamoDB run across several Availability Zones; reads retry with backoff, payments carry idempotency keys and never retry blindly, the gate fails closed, and the index can be rebuilt from the chain |
| Performance efficiency | Each function gets its own memory size, and DynamoDB reads by wallet address, its fastest kind of lookup |
| Cost optimization | Lambda and DynamoDB stay inside their always-free allowances, no NAT gateway runs, the specialists use the cheapest Bedrock tier that passes their cases, every run stops at its ceiling, and AWS Budgets alerts and then denies the agents' roles |
| Sustainability | Nothing runs while idle, and DynamoDB TTL clears stale records |

## Books and curriculum

**The books supply disciplines, not the case study.** *Building the Agentic Enterprise* supplies the register, the gates and the six habits, cited by page. *Building AI Agents for Finance* supplies the agent safety rules in the [reading notes](research/building-ai-agents-for-finance-notes.md). The Solidity documentation, the Foundry Book and Base's documentation supply the chain (P-14).

**The book's Google Cloud stack is swapped for AWS one service at a time.** Its agent framework becomes Strands Agents on AgentCore Runtime, Gemini becomes Bedrock's model tiers, Memory Bank becomes AgentCore Memory, Model Armor becomes Bedrock Guardrails, and its VPC Service Controls perimeter becomes a recorded deviation until Agency Lab holds private data. The full table, with the reason for each swap, is in [P-23](decisions/P-23-aws-platform.md). The one layer the book never covers, agents paying in stablecoins, comes from x402, Base and AWS's own payment service.

The MSAIE's Cloud Applications and Architectures specialization supplies the cloud discipline, and its Blockchain specialization supplies the DeFi risks the scorecard checks. No book or course material goes into Git, because the books' and course's copyright and the Student Code of Conduct bar sharing them, so every fact here cites a public source (P-14).

## Decision Register

**Twenty-five decisions make up the register.** P-01 to P-22 were accepted on November 7, 2026, and P-23 to P-25 on November 8, 2026, when they superseded P-02, P-16 and P-20 and amended the rows marked below. The P prefix keeps them apart from the earlier D-01 to D-26 in the dated record. The book's own register holds fifteen rows and warns that more than thirty means decisions are being argued again, so a new decision takes the next ID, P-26, and a change to an old one edits its row.

| ID | Decision | Status | Why | Revisit when |
| --- | --- | --- | --- | --- |
| P-01 | The case study is an agentic commerce research and education platform with three parts, a toolkit, a research desk and an education track, organized around how agents hold and spend stablecoins | Accepted | Each part feeds the others, and no one covers this subject neutrally today | Before module 1 ships |
| P-02 | Superseded by P-24. Build on Sui from module 1, with every on-chain part written in Move | Superseded | Sui's agent payment rail is testnet-only, and AWS's payment service settles on Base | Not applicable |
| P-03 | Test money only on Base Sepolia: no real-money account, no token and no stablecoin of Agency Lab's own | Accepted; amended by P-24 | Payments are final, beginners copy the build, and issuing a dollar requires a license under the GENIUS Act | After an independent audit |
| P-04 | Research is rail-neutral: one scorecard for every chain and stablecoin, Base included, with Base, Solana and Sui measured side by side. Briefs cover risk, safety and how-to, cite a source for every answer, may say "insufficient evidence", and never make price calls, trade signals or personal recommendations | Accepted; amended by P-24 | A referee that favors its own rail loses the trust that makes its briefs worth buying | Before any paid offer to people |
| P-05 | The agent's spending authority is an allowance the chain enforces through a smart wallet, with a budget, an expiry and an allowed-recipient list the owner can suspend or revoke. Agency Lab writes its own in Solidity in module 5 and compares it with Coinbase Spend Permissions in module 8 | Accepted; amended by P-24 | A limit the chain enforces holds even if every check before it fails | Module 8 |
| P-06 | Control lives outside the model: a write-back gate checks every payment and fails closed. The toolkit's key is created in AWS KMS and never leaves it; the managed path's key is held by its wallet provider through AgentCore payments; no key ever appears in code, prompts or logs | Accepted; amended by P-23 | A fooled model or a crashed check still cannot overspend, and a key the code never holds cannot leak through it | Only ever tightened |
| P-07 | Every payment is bound to its receipt: the x402 settlement response, with its transaction hash, is stored with the request, and escrow covers a service that takes the money and fails to deliver | Accepted; amended by P-24 | An agent never pays without a record of what it bought, and Base cannot settle the payment and the delivery as one step | Module 6 |
| P-08 | Readers onboard with Coinbase embedded wallets and sponsored smart-account gas, and agents pay with x402's signed USDC authorizations, whose gas the facilitator pays | Accepted; amended by P-24 | Beginners never buy gas before a first payment, and agents manage one balance instead of two | Module 7 |
| P-09 | Solidity for on-chain code, tested with Foundry, and Python for everything else: web3.py for the chain, x402's Python SDK for payments, Strands Agents for the agents and AWS CDK for the infrastructure | Accepted; amended by P-24 | Python covers every tool off the chain, and Solidity has the most tutorials and AI coding help for a beginner | If a needed tool has no Python version |
| P-10 | The six safety habits carry over unchanged: release manifest, fail-closed write-back gate, kill switch with named steps and dated drills, test-set gate, near-miss log and per-run cost ceiling | Accepted | None of them depended on the chain or the cloud | Each rung gate |
| P-11 | The chain records what must never be edited, such as allowances, payments and escrow deadlines, and any off-chain index can be rebuilt from it | Accepted | Anyone can verify the money, and losing the index costs nothing | Module 10 |
| P-12 | Superseded by P-20, and P-23 now restores AWS. P-12 had kept AWS as the cloud: KMS for keys, Lambda for the agent, DynamoDB for the index and a budget that blocks the agent's roles | Superseded | P-23 records the current reasons for AWS | Not applicable |
| P-13 | The research charter excludes measuring fake or wash agent activity | Accepted | That work needs data access and legal review Agency Lab won't have, and it would turn a teaching desk into a policing one | Before rung 5 |
| P-14 | The Solidity documentation, the Foundry Book and Base's documentation join the two current books as reading sources, and no book or course material goes into Git | Accepted; amended by P-24 | Solidity replaces Move, and the books' and course's copyright and the Student Code of Conduct bar sharing them | Never, for the Git rule |
| P-15 | The plan stays dateless: modules close on checks, rungs close on gates, and dates return when the capstone course begins | Accepted | A gate holds the bar where a date invites lowering it | When the capstone course begins |
| P-16 | Superseded by P-25. Keep the Ambition name and its public repository, with the GitLab mirror and the MIT License unchanged | Superseded | The platform's subject is agency, and the name now says so | Not applicable |
| P-17 | The paid service charges over x402 on Base Sepolia, through the public testnet facilitator | Accepted; amended by P-24 | x402 has an official Python SDK and Base support, and the testnet facilitator needs no API key | If the testnet facilitator closes |
| P-18 | Apply for Base's Creator Grant Program for the education track, for Base Builder Grants once something ships, and to a later Base Batches startup cohort | Accepted; amended by P-24 | A grant can fund the build and an independent audit, and each program targets work on Base | When each program opens its next round |
| P-19 | Superseded by P-21. The first committee had eight units and four specialists | Superseded | P-21 keeps the book's seven units, with the on-chain payments analysis inside the Sector Specialist | Not applicable |
| P-20 | Superseded by P-23. Google Cloud was the platform: Cloud Run, Firestore, Cloud Workflows, Cloud Scheduler, Cloud KMS, Apigee and a VPC Service Controls perimeter, with Gemini agents and a Claude judge on Vertex AI | Superseded | AWS settles x402 on Base natively, and the book's disciplines do not depend on Google's services | Not applicable |
| P-21 | The research committee has seven units, matching Figure 13.1 of the book: the Research Director; the Market Analyst; the Macro Economist (the book's economist, retooled); the Sector Specialist, which includes the on-chain payments analysis, Base first and then Solana and Sui; the Findings Generator (the book's Thesis Generator); the Compliance Agent as a gate; and the Report Writer. It runs on AgentCore Runtime | Accepted; amended by P-23 and P-24 | Each data domain keeps one owner, and the committee keeps the book's shape: three specialists under the Director | When the agent specifications set each unit's module and cost |
| P-22 | Tests and the kill switch follow the book, scaled to the capstone. Every commit runs a 50-query smoke set; the golden set of 200 or more queries runs when a unit joins and at each rung gate, on Bedrock batch inference; the gate is 0.90 on the golden set and 4.5 on the five-point judge scale; a canary takes 5% of traffic after 24 hours of shadow running. The kill switch runs from a CloudWatch alarm through SNS to a Lambda function that sets a DynamoDB flag, adds an AgentCore Policy rule denying every payment tool, pauses the schedules and denies the agents' roles; API Gateway and every service check the flag | Accepted; amended by P-23 | Full runs at joins and gates catch regressions at a fraction of a nightly run's cost, and the kill switch must stop the gateway as well as the agents | If a regression slips between gates, the nightly run returns |
| P-23 | AWS is the platform, in us-east-1 and serverless first: AgentCore Runtime, Memory, Gateway, Identity, Policy, Evaluations and payments; Bedrock models pinned by tier, with the Compliance judge from a different vendor than the generators; Lambda, Step Functions, EventBridge, DynamoDB, S3, API Gateway, CloudFront and KMS; CDK in Python, deployed by GitHub Actions through OIDC. This supersedes P-20 ([record](decisions/P-23-aws-platform.md)) | Accepted | AWS pays for things on Base natively, keeps everything in Python, and is the cloud the degree teaches | Rung-3 cost and Well-Architected review, or when Agency Lab first holds private data |
| P-24 | Base is the chain, with Base Sepolia as the only network until an independent audit, Solidity for contracts and x402 for paid services. This supersedes P-02 ([record](decisions/P-24-base-chain.md)) | Accepted | Base carries the most x402 dollars, AWS's payment service settles on it, and its funding programs target agentic commerce | Rung-3 review, or if Sui's Agent Payments reaches mainnet with an official x402 kit |
| P-25 | The platform's name is Agency Lab, never "Agency" alone; the repositories are renamed `agency-lab` as a separate step, and the mission and MIT License are unchanged. This supersedes P-16 ([record](decisions/P-25-agency-lab-name.md)) | Accepted | The platform studies and teaches agency, and "Lab" makes a common word searchable and says what the platform is | Only if the mission changes |

## Plain-language terms

| Term | Plain meaning |
| --- | --- |
| AgentCore | AWS's set of managed services for running AI agents: a runtime, memory, a tool gateway, identity, policy, evaluations and payments |
| AgentCore payments | AgentCore's payment service, which pays x402 bills from a Coinbase or Stripe wallet within a session budget |
| Agentic commerce | AI agents buying and selling on their own, paying per request in digital dollars |
| Allowance | The most an agent may spend, for how long and to whom, enforced by a contract |
| API Gateway | An AWS service that gives code a public web address and decides which function answers each request |
| Atomic transaction | A set of steps that all succeed or all fail together, so nothing is left half done |
| AWS Budgets | AWS's spending alarms, which can also block chosen roles once the bill passes a set amount |
| AWS CDK | A toolkit for describing AWS resources in Python code, so the whole setup can be reviewed, tested and rebuilt |
| Base | Coinbase's layer 2 blockchain, built on Ethereum |
| Base Sepolia | Base's free test network, where all of Agency Lab's money is test money |
| Batch inference | Sending model requests in bulk to be answered within hours, at half the usual price for the Bedrock models that offer it |
| Bedrock | AWS's service for calling AI models from several vendors, authorized by AWS roles instead of a separate API key |
| Bedrock Guardrails | Bedrock's filters for prompts and answers, including a check that an answer is grounded in its source |
| Block | A numbered batch of transactions the network has recorded, like a page in its record book |
| CloudWatch | AWS's logs, metrics and alarms service |
| Cost ceiling | The most one agent run may spend on models and services; near it the agent switches to a cheaper model, and at it the run stops |
| DynamoDB | AWS's database that stores records by a key and needs no server to manage |
| Embedded wallet | A wallet created inside an app when a person signs in with email or a social login, with no browser extension |
| Escrow | Holding a payment until the service delivers, then refunding it if a deadline passes |
| EventBridge Scheduler | An AWS service that starts a job at a set time or on a repeating schedule |
| Facilitator | A service that checks an x402 payment and records it on the chain, paying the gas |
| Fail closed | When a check breaks, times out or lacks the data it needs, its answer is no |
| Finality | The point after which a blockchain payment can no longer be reversed |
| Foundry | A toolkit for writing, testing and deploying Solidity contracts |
| Gas | The small fee a blockchain charges to run a transaction, paid on Base in ETH |
| Gasless payment | A payment whose gas someone else pays, so the payer needs only the stablecoin |
| GENIUS Act | The 2025 US law that sets who may issue a payment stablecoin and how it must be backed |
| IAM role | A set of AWS permissions that code takes on for a short time, instead of holding a password or key |
| Kill switch | A fast way to stop an agent: here, revoking its allowance, pausing its schedules, denying its role and blocking its payment tools |
| KMS | AWS Key Management Service, which keeps keys inside secure hardware and signs with them there |
| Lambda | AWS's way to run a function without managing a server; it runs on demand and bills per request |
| Layer 2 | A blockchain that bundles many transactions and settles them on another chain, such as Ethereum, which makes each one cheaper |
| Near-miss log | A record of every payment the gate refused or sent for approval, with its reason, read for warnings before a real loss |
| OIDC | A standard that lets GitHub prove who it is to AWS and receive short-lived credentials, so no AWS key is stored |
| Paymaster | A contract that pays other people's gas, here within a limit Agency Lab sets |
| Rail | The network and rules a payment travels on, such as a blockchain or a card network |
| Release manifest | One file per deploy listing exactly which model, prompts, tools, contracts and allowances are running |
| secp256k1 | The type of cryptographic key Ethereum and Base use to sign transactions |
| Sequencer | The computer that puts a layer 2's transactions in order; on Base, Coinbase runs it |
| Smart account | A wallet run by contract code instead of a single key, so its own rules can limit what it pays and someone else can pay its gas |
| Solidity | The programming language for contracts on Ethereum and Base |
| Spend Permissions | Coinbase's shared contract that lets a smart wallet's owner give a spender an allowance per token and per time window |
| Stablecoin | A token designed to hold a steady value, such as USDC at one US dollar |
| Step Functions | AWS's service for running a multi-step process in order, with retries and waits |
| Strands Agents | AWS's open-source Python framework for building agents |
| Synthetic dollar | A token that tracks a dollar through offsetting trades rather than cash reserves |
| Test network | A practice blockchain where all money is free and worthless |
| Test set | A fixed list of tasks with known right answers that every change must pass |
| Traffic class | A tag on every model call saying what it was for, such as an agent run, a test or a reader request, so costs can be split by purpose |
| Transaction hash | The unique ID of a transaction, used to look it up on a block explorer |
| Validator | A computer that checks and records a blockchain's transactions |
| Well-Architected Framework | AWS's six-pillar checklist for judging a cloud design |
| Write-back gate | The checkpoint between what an agent proposes and anything that changes the world, such as a payment |
| x402 | An open standard for paying per request over the web's "402 Payment Required" response, governed by its own foundation |
| X-Ray | AWS's tracing service, which follows one request through every service it touches |

## Sources

- Agency Lab decision records [P-23](decisions/P-23-aws-platform.md), [P-24](decisions/P-24-base-chain.md) and [P-25](decisions/P-25-agency-lab-name.md), each with its own sources
- Jaroslav Pantsjoha, [*Building the Agentic Enterprise*](https://www.oreilly.com/library/view/building-the-agentic/9781807604455/) (Packt, September 2026), for the register, gates and six habits, cited by page
- Hanane Dupouy and Fayssal El Mofatiche, [*Building AI Agents for Finance*](https://reference-global.com/book/9781837022281) (Packt, 2026), with Agency Lab's adopted rules in the [reading notes](research/building-ai-agents-for-finance-notes.md)
- Rothschild et al., [The Agentic Economy (arXiv:2505.15799, 2025)](https://arxiv.org/abs/2505.15799), and Tomasev et al., [Virtual Agent Economies (arXiv:2509.10147, 2025)](https://arxiv.org/abs/2509.10147), for the two candidate habits above; both are conceptual framing, not measured results
- Sui Foundation, [Blockchain for AI agents and agentic commerce](https://sui.io/blog/blockchain-for-ai-agents-agentic-commerce-sui) (September 2, 2026), the source of the scorecard's first four questions
- Jones Day, [US Treasury proposes GENIUS Act rules for stablecoin issuance, offer and sale](https://www.jonesday.com/en/insights/2026/08/us-treasury-proposes-genius-act-rules-for-stablecoin-issuance-offer-and-sale) (August 2026)
- Blockworks, [$160M in stolen funds puts Sui's decentralization to the test](https://blockworks.co/news/suis-decentralization-dex-put-to-the-test), on the Cetus exploit and the validator freeze
- The Block, [Base is 'permissionless,' says Coinbase's Jesse Pollak](https://www.theblock.co/amp/post/244629/coinbase-base-jesse-pollak), on Coinbase as Base's sole sequencer operator
- Gitcoin, [Base Ecosystem Fund](https://gitcoin.co/apps/base-ecosystem-fund), on Aerodrome and Morpho in Base's DeFi stack
- Circle, [Transparency](https://www.circle.com/en/transparency), on USDC's reserves and monthly examinations, and Ethena, [Custodian attestations](https://docs.ethena.fi/resources/custodian-attestations), on USDe
- Coinbase Developer Platform, [Spend Permissions](https://docs.cdp.coinbase.com/wallet-api/v2/evm-features/spend-permissions), [Paymaster](https://docs.cdp.coinbase.com/paymaster/introduction/welcome) and [Embedded wallet smart accounts](https://docs.cdp.coinbase.com/embedded-wallets/evm-features/smart-accounts)
- Base, [Accepting payments](https://docs.base.org/ai-agents/payments/accepting-payments), on the public testnet facilitator, and Blockscout, [x402 payments](https://docs.blockscout.com/devs/x402-payments), on the Python SDK
- Circle, [Testnet faucet](https://faucet.circle.com), which lists Base Sepolia for test USDC
- AWS, [What is Amazon Bedrock AgentCore?](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html) and [AgentCore payments](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments.md)
- AWS, [Well-Architected Framework, Sustainability Pillar](https://docs.aws.amazon.com/wellarchitected/latest/sustainability-pillar/sustainability-pillar.html), which lists the six pillars
- Chainlink, [AWS KMS Signer](https://docs.chain.link/crec/guides/signers/aws-kms), on signing with a secp256k1 key that never leaves AWS's hardware
- GitHub, [Configuring OpenID Connect in Amazon Web Services](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)
- AWS, [Configuring budget actions](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-controls.html), [Lambda quotas](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html) and [Using time to live in DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html)
- OWASP GenAI Security Project, [OWASP Top 10 for Agentic Applications for 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications/) (December 9, 2025)
- Agency Lab, [Build in Public: Mission and Ladder](build-in-public-plan.md), the modules, ladder and gates in plan form
