# P-23: AWS replaces Google Cloud as Agency Lab's platform

Nov 8, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 8, 2026 |
| Supersedes | P-20 (Google Cloud) |
| Amends | P-06 (where the key lives), P-21 (where the committee runs) and P-22 (tests and the kill switch) |
| Related | [P-24](P-24-base-chain.md) (Base) and [P-25](P-25-agency-lab-name.md) (the name) |

## Summary

**Agency Lab moves from Google Cloud to AWS, because AWS pays for things on Base natively and the book's lessons never depended on Google's services.** *Building the Agentic Enterprise* teaches its disciplines through Google Cloud, but its author says its patterns are designed not to depend on any one foundation (p. 637), and its 774 pages hold only about a dozen import lines from Google's agent framework. The one layer Agency Lab adds, agents paying in stablecoins, is the layer the book leaves out: it never mentions x402, blockchains or stablecoins, and only one agent in its case study touches payments at all (Table 12.4, pp. 633–634). Amazon Bedrock AgentCore payments fills that gap, because it settles x402 payments in USDC on Base, including Base Sepolia, the test network Agency Lab uses.

The swap keeps the book's register, gates and six habits and changes only the services underneath them. Python stays the language for every agent, every tool and the infrastructure code, and GitHub Actions stays the only way anything is deployed.

## Context

P-20, accepted on November 7, 2026, adopted the book's Google Cloud reference build: Cloud Run, Firestore, Cloud Workflows, Apigee, a VPC Service Controls perimeter, Gemini agents on Vertex AI and a Claude judge. Three facts changed the case for it.

First, the chain moved to Base under P-24. On Base, AWS offers a managed payment service built with Coinbase and Stripe, while Google's payment work runs through AP2 and UCP, protocols that mostly ride card networks. Second, the book's own framework comparison concedes that every framework it reviews runs on any cloud as a container, and that its framework's advantage is native deployment on Google Cloud rather than anything an agent does (pp. 377–378). Third, the MSAIE's Cloud Applications and Architectures specialization teaches AWS, so the capstone practices the cloud the degree teaches, which was the reason AWS first joined the plan on November 4 (archived decision D-17).

## Decision

**Agency Lab runs on AWS in one region, us-east-1, serverless first.** Infrastructure is AWS CDK code in Python, deployed by GitHub Actions through OIDC, so no long-lived AWS key exists anywhere. Each Google Cloud piece the book uses gets one AWS counterpart:

| The book on Google Cloud | Agency Lab on AWS | Why this one |
| --- | --- | --- |
| Agent Development Kit (ADK) on Agent Runtime | Strands Agents, AWS's open-source Python framework, on AgentCore Runtime | AgentCore Runtime hosts ADK too, but AgentCore Memory and AgentCore payments integrate with Strands and LangGraph, not ADK, so ADK would be a second-class citizen |
| Gemini Flash and Pro tiers | Amazon Bedrock model tiers, pinned by tier in the release manifest, following the book's decision 9 to pin model tiers rather than model IDs (p. 704) | Bedrock's IAM roles authorize every call, so there is no model API key to leak, and batch inference costs half the on-demand price for the models that offer it |
| Claude judge on Vertex AI | Claude on Bedrock, with the committee's generators on a different vendor's models (Amazon Nova by default) | P-20's rule survives: a judge from a different vendor than the text it grades avoids self-preference |
| Agent Runtime Sessions and Memory Bank | AgentCore Memory | Short- and long-term memory without a database to run |
| Managed MCP tool gateway and Agent Identity | AgentCore Gateway and AgentCore Identity | The gateway also mounts Coinbase's x402 Bazaar, a catalog of paid endpoints agents can discover |
| Action guardrails and A2A middleware | AgentCore Policy, which intercepts every Gateway tool call against Cedar rules | A payment tool can be denied in one place, which also serves the kill switch |
| Model Armor and the Vertex grounding check | Bedrock Guardrails, including its contextual grounding check | One service filters prompts and outputs and scores whether each answer is grounded in its source |
| Agent Evaluation service | AgentCore Evaluations, online and on demand | It scores sessions, responses and tool calls from the traces the agents already emit |
| Cloud Logging, Trace and Monitoring | CloudWatch, X-Ray and AgentCore Observability | All three read the same OpenTelemetry traces |
| Cloud Run | AWS Lambda for tools and services, with Fargate for runs past Lambda's 15 minutes | Lambda bills per request and leaves patching to AWS |
| Cloud Workflows and Cloud Scheduler | Step Functions and EventBridge Scheduler | Durable fan-out, retries and waits for human approval |
| Pub/Sub and Eventarc | EventBridge, SNS and SQS | Events move between services without direct calls |
| Firestore | DynamoDB | Fast reads by key, Streams for alerts, rebuilt from the chain if lost |
| BigQuery audit and billing export | S3 with Athena for the audit record, and AWS Cost Explorer and Budgets for billing | Append-only files that SQL can query, at almost no idle cost |
| Cloud KMS | AWS KMS, with a secp256k1 key, the type Base uses | The key is created inside KMS and signs there, so it never leaves AWS's hardware |
| Apigee | Amazon API Gateway | Gives the paid x402 service a public address with rate limits |
| Firebase Hosting | S3 behind CloudFront | The bucket stays private and the page stays fast |
| Terraform and Cloud Build | AWS CDK in Python and GitHub Actions | One language for the app and its infrastructure |
| Workload Identity Federation | GitHub OIDC into IAM roles | Short-lived credentials replace stored keys |
| VPC Service Controls perimeter | Not built now; a recorded deviation | AWS has no single counterpart, so a perimeter means service control policies, resource control policies and VPC endpoint policies, and nothing private needs one yet |
| Grounding with Google Search | Paid search bought over x402 with the toolkit's own payments | The research desk buys its evidence the same way it teaches agents to pay |
| AP2 and UCP for commerce | x402 through AgentCore payments, with AP2 kept as a subject the scorecard studies | AP2 already has an x402 extension, so nothing is lost by settling on x402 |

**Two payment paths run side by side and are compared in module 9.** The toolkit's own path, which modules 1 to 8 build, signs with a key created inside AWS KMS (P-06). AgentCore payments, the managed path, signs through a Coinbase CDP or Stripe Privy wallet whose key that provider holds, and it caps each payment session with a budget and an expiry. Neither path ever puts a key in Agency Lab's code, prompts or logs. Agency Lab teaches both, publishes the comparison, and lets the research desk use whichever passes its gate cases.

**P-22 changes with the platform.** Every commit still runs the 50-query smoke set, but the 200-plus-query golden set no longer runs nightly. It runs only when a unit joins the committee and at each rung gate, on Bedrock batch inference, at half price for the models that offer it, which keeps test costs close to the minimum the capstone needs. The kill switch runs from a CloudWatch alarm through SNS to a Lambda function that sets a flag in DynamoDB, adds an AgentCore Policy rule that denies every payment tool, pauses the EventBridge schedules and applies an IAM deny to the agents' roles. API Gateway and every service check the flag before acting.

## Consequences

**Agency Lab gets payments, identity, memory, policy and evaluation as managed services in one account,** so the build spends its effort on the toolkit and the research instead of on plumbing. Everything an agent does stays in Python, the language the curriculum and the reader challenges already use.

**Some of Google's integration is lost.** AWS has no single equivalent of VPC Service Controls, no counterpart to Google's low-code agent studio, and no Google Search grounding, and the book's code examples need translating from ADK into Strands. The perimeter returns as a recorded deviation, to be revisited when Agency Lab first holds private data.

**The cost reference returns to Bedrock, and it is higher than a few cents a run.** The November 6 research priced the earlier eight-agent committee on Claude at about $1.00 for a standard run, or about $1.10 with Bedrock's 10% regional premium, and proposed a provisional ceiling of $2.15, with module 12's single unit at about $0.35 ([research report](../research/research-engine-research-report.md)). The book's own three-agent pipeline costs $0.15 to $0.40 a thesis (p. 109). Putting the specialists on the cheapest Bedrock tier and keeping the reasoning tier for synthesis will lower those figures, and the ceiling is set by measurement under P-10 before any unit joins.

**Concentration risk rises, because Coinbase now sits under the chain, the wallets, the paid-service catalog and the facilitator.** The book warns that a vendor can change a core dependency on its own schedule (p. 637). Two mitigations follow: x402 is governed by its own foundation under LF Projects, and the rail-neutral scorecard asks Base the same freeze and halt questions it asks every other rail (P-04).

## Alternatives considered

| Option | Why not |
| --- | --- |
| Stay on Google Cloud (P-20) | Its strengths, Gemini and the integrated agent platform, sit beside the payment layer rather than in it, and it would need a separate wallet stack for Base |
| Split clouds: agents on Google Cloud, payments on AWS | Two identity systems, two networks and two observability stacks; the book itself warns that protocols do not remove the infrastructure problem underneath them (p. 157) |
| AWS without AgentCore: Lambda, Step Functions and Bedrock only | Kept as the fallback for any AgentCore service that fails its gate cases, but it rebuilds memory, gateway and policy by hand, which the book calls building tomorrow's legacy (p. 379) |

## Revisit when

At the rung-3 cost and Well-Architected review; if AgentCore payments stops supporting Base Sepolia; if Bedrock lacks a model tier a unit needs; or when Agency Lab first stores private data, which brings the data perimeter back.

## Sources

- Jaroslav Pantsjoha, [*Building the Agentic Enterprise*](https://www.oreilly.com/library/view/building-the-agentic/9781807604455/) (Packt, September 2026), cited by page; no book text is stored in this repository (P-14)
- AWS, [What is Amazon Bedrock AgentCore?](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html), on Runtime, Memory, Gateway, Policy, Evaluations and the frameworks each supports
- AWS, [Amazon Bedrock AgentCore payments](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments.md), on x402 and MPP, payment limits, CoinbaseCDP and Stripe Privy wallets and the x402 Bazaar
- AWS, [AgentCore payments is now generally available](https://aws.amazon.com/about-aws/whats-new/2026/08/bedrock-agentcore-payments-ga/) (August 18, 2026)
- AWS, [Fund an AgentCore payments wallet](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments-fund-wallet.html), on testnet funding with Circle's faucet on Base Sepolia
- AWS News Blog, [AgentCore adds quality evaluations and policy controls](https://aws.amazon.com/blogs/aws/amazon-bedrock-agentcore-adds-quality-evaluations-and-policy-controls-for-deploying-trusted-ai-agents/), with Policy generally available March 3, 2026 and Evaluations March 31, 2026
- AWS, [Amazon Bedrock pricing](https://aws.amazon.com/bedrock/pricing/), on batch inference at 50% below on-demand for select models
- AWS, [Contextual grounding check in Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-contextual-grounding-check.html)
- AWS, [Data perimeters on AWS](https://aws.amazon.com/identity/data-perimeters-on-aws/), on service control policies, resource control policies and VPC endpoint policies
- AWS, [Configuring budget actions](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-controls.html), on applying an IAM policy when a budget passes its threshold
- Chainlink, [AWS KMS Signer](https://docs.chain.link/crec/guides/signers/aws-kms), on signing with an `ECC_SECG_P256K1` KMS key
- GitHub, [Configuring OpenID Connect in Amazon Web Services](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)
- Linkup, [x402 payments](https://docs.linkup.so/pages/documentation/platform/x402.md), an example of search bought per request in USDC on Base
- Agency Lab, [research engine research report](../research/research-engine-research-report.md) (November 6, 2026), the Bedrock cost estimates
