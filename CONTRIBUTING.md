# Contributing to Ambition

Thanks for helping. Ambition is built in public, so questions, fixes and ideas are all welcome, and small changes are the easiest to review.

## Where to contribute

Open issues and pull requests on GitHub at [github.com/dinkycoder/ambition](https://github.com/dinkycoder/ambition). The copy at [gitlab.com/dinkycoder/ambition](https://gitlab.com/dinkycoder/ambition) is an automatic mirror that GitHub overwrites on every change, so anything opened or merged there is lost.

## Safety rules

These apply to every issue, pull request, comment and screenshot.

1. **Test money only.** Everything runs on Base Sepolia, a free test network. Never point Ambition at real money.
2. **No secrets, ever.** Never commit, paste or screenshot a wallet key, seed phrase or API key. If one slips in, treat it as stolen: move any funds and replace the key at once, because deleting the commit doesn't remove it from history.
3. **Report security problems privately.** Don't post the details of a vulnerability in public. Open an issue that says only that you found one, and you'll be contacted privately.

## How to propose a change

1. **Start with an issue** for anything bigger than a typo, so we can agree on the approach before you write it.
2. **Keep each pull request to one change**, and say what it does and why in plain words.
3. **Include tests** for code once the library has them, and make sure the existing ones still pass.
4. **Expect a review.** Every change, including ones proposed by AI agents, is approved by the maintainer before it is merged.

## Design rules

Changes to anything a person sees follow the [design system](design-system/README.md) and the [design guidelines](docs/design-guidelines.md). The ones most often missed:

1. **Use tokens, never raw values**, for color, spacing, type, shape and motion.
2. **Every spend, approval or signature goes through `SpendConfirmation`**, which shows the amount, the recipient, the network and that the payment is final.
3. **No pressure.** Scarcity, countdowns, streak counters, decoy choices, preset amounts, pre-selected choices, loss framing and sunk-cost appeals are banned everywhere.
4. **Accessible by default.** Text meets 4.5:1 contrast in every theme (7:1 in high contrast), everything works by keyboard and screen reader, and color is never the only signal.
5. **Plain words.** Use the glossary terms, define each one at first use, and name the action and the amount on every money button.

## License

By contributing, you agree that your contribution is released under the [MIT License](LICENSE), the same license as the rest of Ambition.

## Be kind

Assume good intent, explain rather than correct, and remember that many readers are new to blockchains. Learning in public only works when it is safe to ask basic questions.
