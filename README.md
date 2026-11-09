# Agency Lab

**Help AI builders give their agents money safely, one small win at a time.**

Agency Lab is an open-source agentic commerce research and education platform on AWS and Base: a toolkit that lets AI agents hold and spend stablecoins safely, a research desk that scores payment rails and stablecoins on one neutral scorecard, and lessons that teach both. It is built in public one module at a time, with contracts in Solidity and everything else in Python, and each module ends with a reader challenge anyone can prove they did. It climbs a ladder whose rungs end at gates rather than dates. It is also an MSAIE capstone project, and its dates return when the capstone course begins.

It grows in modules: agent wallets whose keys never leave AWS KMS, allowances a smart wallet enforces, x402 payments bound to their receipts, gasless stablecoin payments, money-back escrow, statements and spending alerts. Its design system adds the money components that agent-payments apps need, on top of IBM's open-source Carbon.

The name comes from *Building the Agentic Enterprise*, whose author observes that the feedback in an agent's reason-act-observe loop is what separates agency from ambition. Agency Lab was called Ambition until November 8, 2026 ([P-25](docs/decisions/P-25-agency-lab-name.md)).

## What's here

| Path | What it is |
| --- | --- |
| [docs/build-in-public-plan.md](docs/build-in-public-plan.md) | The mission, the least-to-most ladder, the twelve modules, what we measure, the UX agent and the ground rules |
| [docs/roadmap.md](docs/roadmap.md) | The roadmap on AWS and Base: why this platform, the case study, the ladder, the twelve modules, the rail-neutral scorecard, six safety habits, the architecture and the Decision Register |
| [docs/decisions/](docs/decisions/) | Decision records for the November 8, 2026 changes: [P-23](docs/decisions/P-23-aws-platform.md) (AWS replaces Google Cloud), [P-24](docs/decisions/P-24-base-chain.md) (Base replaces Sui) and [P-25](docs/decisions/P-25-agency-lab-name.md) (the Agency Lab name) |
| [docs/archive/](docs/archive/) | Earlier roadmaps and specifications kept unchanged as dated records: the Base and Solidity roadmap of November 4 (D-01 to D-26), and the Sui and Google Cloud roadmap and agent specifications of November 7 |
| [docs/design-guidelines.md](docs/design-guidelines.md) | Principles and persuasion policy, foundations, brand assets, components, screen patterns, the reader journey, glossary and maintenance |
| [design-system/](design-system/) | The style guide, design tokens (`tokens.json`, `tokens.css`) and previews of the ten money components |
| [docs/research/usability-testing-plan.md](docs/research/usability-testing-plan.md) | Research on free and low-cost usability testing (UXtweak, Figma Make and alternatives) and the testing plan by module |
| [docs/research/participant-consent-form.md](docs/research/participant-consent-form.md) | The consent form every usability-study participant reads and signs, covering recordings, data protection and their rights |
| [docs/research/building-ai-agents-for-finance-notes.md](docs/research/building-ai-agents-for-finance-notes.md) | Reading notes on *Building AI Agents for Finance* (Packt, 2026): the rules from the book that Agency Lab adopts, with page numbers |
| [docs/research/research-engine-agent-specs.md](docs/research/research-engine-agent-specs.md) | Specifications for the research desk's seven units on AWS: the order they join the ladder, their sources, tools, gate tests, failure modes and how the per-run ceiling is measured |
| [docs/research/research-engine-research-report.md](docs/research/research-engine-research-report.md) | The November 6 research behind those specifications, with every source and every page that could not be opened |
| [docs/pdf/](docs/pdf/) | PDF versions of the plan, the roadmap and Decision Register, the decision records, the guidelines, the design system, the testing plan, the consent form, the reading notes and the research engine specifications |

Code arrives module by module, starting with the agent wallet in module 1.

## Safety

Everything runs on Base Sepolia, Base's free test network, with test money only. No wallet key, seed phrase or API key ever goes into this repository or a post: the agent's key is created inside AWS KMS and signs there. Agency Lab issues no token and no stablecoin. Never share a seed phrase with anyone.

## Contributing

The main copy of Agency Lab lives on GitHub. [gitlab.com/dinkycoder/ambition](https://gitlab.com/dinkycoder/ambition) is an automatic mirror that GitHub overwrites on every change, so please open issues and pull requests on [GitHub](https://github.com/dinkycoder/ambition). Both repositories keep the address `ambition` until they are renamed `agency-lab` under P-25, and GitHub will redirect the old address. [CONTRIBUTING.md](CONTRIBUTING.md) covers the safety rules, how to propose a change and the design rules.

## License

Agency Lab is released under the [MIT License](LICENSE), which covers the code, docs and design system in this repository. The license doesn't cover the Agency Lab name or any future logo.
