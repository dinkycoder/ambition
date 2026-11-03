# Ambition

**Help AI builders give their agents money safely, one small win at a time.**

Ambition is an open-source toolkit for giving AI agents money safely on a test blockchain. It is built in public over 12 weeks, from November 2, 2026 to a demo on January 26, 2027, with one LinkedIn post and one reader challenge each week, and it is also an MSAIE capstone project.

It grows in modules: agent wallets, x402 payments (Coinbase's standard for agents paying on the web), spending limits, money-back escrow, statements and spending alerts. Its design system adds the money components that agent-payments apps need, on top of IBM's open-source Carbon.

## What's here

| Path | What it is |
| --- | --- |
| [docs/build-in-public-plan.md](docs/build-in-public-plan.md) | The mission, the least-to-most ladder, the 12-week plan, what we measure, the UX agent and the ground rules |
| [docs/design-guidelines.md](docs/design-guidelines.md) | Principles and persuasion policy, foundations, brand assets, components, screen patterns, the reader journey, glossary and maintenance |
| [design-system/](design-system/) | The style guide, design tokens (`tokens.json`, `tokens.css`) and previews of the ten money components |
| [docs/research/usability-testing-plan.md](docs/research/usability-testing-plan.md) | Research on free and low-cost usability testing (UXtweak, Figma Make and alternatives) and the 12-week testing plan |
| [docs/research/participant-consent-form.md](docs/research/participant-consent-form.md) | The consent form every usability-study participant reads and signs, covering recordings, data protection and their rights |
| [docs/pdf/](docs/pdf/) | PDF versions of the plan, the guidelines, the design system, the testing plan and the consent form |

Code arrives week by week, starting with the agent wallet in week 1.

## Safety

Everything runs on Base Sepolia, a free test network, with test money only. No wallet key, seed phrase or API key ever goes into this repository or a post. Never share a seed phrase with anyone.

## Contributing

The main copy of Ambition lives on GitHub. [gitlab.com/dinkycoder/ambition](https://gitlab.com/dinkycoder/ambition) is an automatic mirror that GitHub overwrites on every change, so please open issues and pull requests on [GitHub](https://github.com/dinkycoder/ambition). [CONTRIBUTING.md](CONTRIBUTING.md) covers the safety rules, how to propose a change and the design rules.

## License

Ambition is released under the [MIT License](LICENSE), which covers the code, docs and design system in this repository. The license doesn't cover the Ambition name or any future logo.
