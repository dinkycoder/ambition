# Ambition

**Help AI builders give their agents money safely, one small win at a time.**

Ambition is an open-source agentic commerce research and education platform on Sui: a toolkit that lets AI agents hold and spend stablecoins safely, a research desk that scores payment rails and stablecoins on one neutral scorecard, and lessons that teach both. It is built in public one module at a time in Move, each module with a reader challenge anyone can prove they did, and it climbs a ladder whose rungs end at gates rather than dates. It is also an MSAIE capstone project, and its dates return when the capstone course begins.

It grows in modules: agent wallets, Move packages on Sui's test network, spending caps the agent holds as objects, payments that settle with their receipts, gasless stablecoin payments, money-back escrow, statements and spending alerts. Its design system adds the money components that agent-payments apps need, on top of IBM's open-source Carbon.

## What's here

| Path | What it is |
| --- | --- |
| [docs/build-in-public-plan.md](docs/build-in-public-plan.md) | The mission, the least-to-most ladder, the twelve modules, what we measure, the UX agent and the ground rules |
| [docs/roadmap.md](docs/roadmap.md) | The roadmap for agentic commerce on Sui: why this platform, the case study, the ladder, the twelve modules in Move, the rail-neutral scorecard, six safety habits, the AWS and Sui architecture and the Decision Register |
| [docs/archive/](docs/archive/) | The earlier Base and Solidity roadmap and its D-01 to D-26 register, kept unchanged as a dated record |
| [docs/design-guidelines.md](docs/design-guidelines.md) | Principles and persuasion policy, foundations, brand assets, components, screen patterns, the reader journey, glossary and maintenance |
| [design-system/](design-system/) | The style guide, design tokens (`tokens.json`, `tokens.css`) and previews of the ten money components |
| [docs/research/usability-testing-plan.md](docs/research/usability-testing-plan.md) | Research on free and low-cost usability testing (UXtweak, Figma Make and alternatives) and the testing plan by module |
| [docs/research/participant-consent-form.md](docs/research/participant-consent-form.md) | The consent form every usability-study participant reads and signs, covering recordings, data protection and their rights |
| [docs/research/building-ai-agents-for-finance-notes.md](docs/research/building-ai-agents-for-finance-notes.md) | Reading notes on *Building AI Agents for Finance* (Packt, 2026): the rules from the book that Ambition adopts, with page numbers |
| [docs/pdf/](docs/pdf/) | PDF versions of the plan, the roadmap and Decision Register, the guidelines, the design system, the testing plan, the consent form and the reading notes |

Code arrives module by module, starting with the agent wallet in module 1.

## Safety

Everything runs on Sui's test network, with test money only. No wallet key, seed phrase or API key ever goes into this repository or a post: the agent's key is created inside AWS KMS and signs there. Ambition issues no token and no stablecoin. Never share a seed phrase with anyone.

## Contributing

The main copy of Ambition lives on GitHub. [gitlab.com/dinkycoder/ambition](https://gitlab.com/dinkycoder/ambition) is an automatic mirror that GitHub overwrites on every change, so please open issues and pull requests on [GitHub](https://github.com/dinkycoder/ambition). [CONTRIBUTING.md](CONTRIBUTING.md) covers the safety rules, how to propose a change and the design rules.

## License

Ambition is released under the [MIT License](LICENSE), which covers the code, docs and design system in this repository. The license doesn't cover the Ambition name or any future logo.
