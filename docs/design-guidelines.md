# Ambition Design Guidelines

Nov 4, 2026 · @dinky

**These are the rules Ambition's UX agent follows and that any builder may reuse.** The style guide comes before any screen, the base is Carbon with Ambition's own look, a persuasion policy protects consent, and Ambition adds the money components that agent-payments apps need. The guidelines ship in numbered releases with the code, and every do-and-don't pair runs as an automated test.

## Principles and persuasion policy

**Five principles decide every design choice, and they come before the style guide.**

1. **Consent before money moves.** Nothing spends, approves or signs without a plain-language confirmation showing the amount, recipient, network and the fact that the payment is final.
2. **Truth over polish.** Every amount links to its blockchain record, and a failed read shows as a failure, never as zero.
3. **Safe by default.** Limits start low, alerts start on, nothing is pre-approved, and amounts and recipients start empty.
4. **Plain words.** One term per concept, defined the first time it appears.
5. **Usable by everyone.** WCAG AA contrast, full keyboard and screen-reader support, and color never the only signal.

**The persuasion policy says which psychological effects the agent may use, and where.** Names follow the UI Patterns library.

| Where | Allowed | Banned |
| --- | --- | --- |
| Learning content and reader challenges | Curiosity, Set Completion, Zeigarnik Effect, Need for Closure, IKEA effect, Peak-end rule, Levels, Fresh Start Effect, verified Achievements | Streak counters, Variable Rewards, gambling-like loops, any challenge that needs real money |
| Money screens | Chunking, Sequencing, Recognition over Recall, Picture Superiority, Reduction, Tunnelling, Limited Choice, Choice Closure, neutral Framing, allowed only while the amount, recipient, finality and Cancel stay visible | Anchoring with preset amounts, pre-selected choices, loss framing, Priming, Delay Discounting |
| Everywhere | Plain facts, such as a deadline stated as a date and time | Scarcity, Limited duration countdowns, Decoy Effect, Inaction Inertia, Sunk Cost appeals, Value Attribution, Illusion of control, Hedonic Adaptation, Nostalgia Effect, testimonials and any unverified social proof |

**Any new use passes one test: would users still agree if they were shown exactly how and why it was presented?**

Some effects justify safeguards rather than tactics. The Cashless Effect makes intangible payments feel smaller, which is also why agents overspend, so screens show dollar amounts and ask for confirmation. Status-Quo Bias makes defaults stick, so defaults are safe. Optimism Bias makes people expect success, so confirmations show the most they could lose. Illusion of control makes people assume an undo exists, so screens say payments are final. Need for Closure turns an unclear status into a second payment, so pending, confirmed, failed and refunded are always shown explicitly.

## Foundations

**The style guide is written in module 8, before the first screen, so every later part inherits it.** Ambition keeps the structure of [Carbon](https://www.carbondesignsystem.com/), IBM's open-source design system, and replaces its look. Screens then behave like a mature system without looking like an IBM product.

| Foundation | Rule | From Carbon |
| --- | --- | --- |
| Tokens | Stored in the [W3C Design Tokens format](https://www.designtokens.org/) (first stable version, October 2025). Names are roles, such as background, layer, text-primary and support-error, never raw values. | Keep the role names and state rules, translated from Carbon's Sass and JavaScript tokens |
| Color | OKLCH values in even lightness steps, with light, dark and high-contrast modes switchable while the app runs. Contrast is tested after conversion to standard screen color (sRGB): 4.5:1 for text, 3:1 for large text, icons and focus rings. Red, amber and green mean status only and are never brand colors. Charts use a four-color set or a single hue, never status colors. | Replace every value and skip Carbon's chart order, which puts red and green in series 5 to 7 |
| Type | System fonts first, for speed, on Carbon's product type scale at weights 400 and 600. A variable font with optical sizing appears only on brand pieces. Every amount uses tabular figures, wallet addresses show in groups of four (0x8f3a 2c91 … 7d04), and text is sentence case. | Keep the scale and drop IBM Plex |
| Spacing and grid | One 4-point unit using Carbon's steps of 4, 8, 12, 16, 24, 32, 40, 48, 64, 80 and 96 px, with 2 px for hairlines only. Carbon's 2x grid has 16 columns on an 8 px unit with breakpoints at 320, 672, 1056, 1312 and 1584 px, but a phone layout and a desktop layout are enough for modules 9 to 12. Line heights snap to 4 px. Grids are set before any screen is drawn, and breaking one needs a stated reason. | Adopt |
| Motion | Carbon's productive durations (70, 110, 150 and 240 ms) with its standard, entrance and exit easing. Each money state (pending, confirmed, failed, refunded) has one consistent cue, and all motion stops when the user turns on reduced motion. | Adapt, adding the reduced-motion rule Carbon's motion page leaves out |
| Icons | An open icon set such as Lucide or Phosphor, and each icon carries the name a screen reader speaks. The verified, spend, refund and test-network icons are reserved for one meaning each. Icons at 16 and 24 px are hand-tuned, not scaled down. | Replace, and use no IBM marks or pictograms |
| Surfaces | Dark mode shows depth through background layers. High-contrast mode uses borders, because shadows barely show there. | Adapt |

Any product can re-skin Ambition by supplying its own token values, because the role names never change.

## Brand assets and identity

**Ambition's icon and logo follow the method of Google's Visual Assets Guidelines, not Google's look.** Each rule is shown as a do-and-don't pair, because paired examples are what an AI agent follows best, and every pair doubles as an automated test.

| Asset | Rule |
| --- | --- |
| Icon | Reductive, geometric, front-facing and flat, and drawn on the pixel grid so it stays crisp. It is redrawn by hand at 16 and 32 px for the browser tab and the GitHub avatar, not shrunk. |
| Logo lockup | The icon plus the name Ambition. As space shrinks it steps down from the full lockup to the icon with a short name, then to the icon alone. Minimum size and clear space are set in multiples of the icon's height. |
| Color versions | Full color, one color, and one color reversed on dark backgrounds, with a short list of approved backgrounds. Status colors never appear in the mark. |
| Sizes | One table covers the browser tab, the GitHub avatar and social preview, LinkedIn post images and the documentation header. |
| What not to copy | Google's four-color palette, its long 45-degree shadows, and anything that makes Ambition look like an IBM or Google product. |

**Identity extends past the logo.** AI agents never see a logo, so Ambition's name, its one-sentence description and the same structured details appear identically in agent registries, on payment pages, in the README and in chat answers. Official images carry content credentials under the C2PA standard, so anyone can confirm they are genuine. The open-source license covers the code but not the name or the logo, so Ambition's mark stays yours.

## Components

**Carbon supplies the general components, and Ambition builds the money components Carbon lacks.** Those money components are Ambition's main public contribution.

| Need | Carbon component | Change for money |
| --- | --- | --- |
| Statements and refunds | Data table: sort, filter, search, expandable rows, batch actions, zebra rows | Amounts align on the decimal point, pages are labeled by month, and an expanded row shows the transaction digest and checkpoint |
| Spend confirmation | Danger modal, with a structured list for the summary | Cancel sits on the left with first focus, overriding Carbon's default. The primary button names the action and amount, such as "Send 5 test USDC". Esc always means cancel. |
| Payment progress | Inline loading | Separate "sent" and "confirmed" states, with the button disabled until the payment finishes, so a second click can't send twice |
| Alerts and results | Inline and actionable notifications | Failures and spending alerts stay until dismissed, and no money message disappears on a timer |
| Status labels | Tag, following Carbon's status-indicator pattern | Color, shape and a text label together |
| Explainers | Toggletip | Plain-language definitions. Essential information never sits in a tooltip. |
| Everyday controls | Button, text input, dropdown, toggle, search, date picker, tabs, content switcher, pagination, tile, code snippet | Toggles only for instant, reversible changes such as pausing alerts |
| Avoided | Number input and progress bar | The number input's arrow keys can nudge an amount, and the progress bar cannot reset, so Ambition's own parts replace both |

**Ambition builds nine money components:**

- **Amount input:** a text field with its unit, six decimals and no stepper, which shows the value back for confirmation.
- **Address display:** groups of four with the first and last groups highlighted, a format check (0x and 64 characters), a copy button, the full value on request, and output a screen reader can read.
- **Transaction status:** submitted, confirming, final, failed and refunded, each with its own shape, icon and label.
- **Spend meter:** spend against a daily limit that resets.
- **Limit editor:** the sentence "Let \[agent\] spend \[5\] USDC per \[day\]".
- **Test-network badge:** shown in the header on every screen.
- **Deadline display:** a fixed date and time, never a ticking timer.
- **Money empty states:** no data, no results, and error. A failed read never shows as $0.
- **Agent-proposal label:** Carbon's AI label on every spend the agent proposes, with an explanation of why it proposed it.

**Behavior rules apply across all components.**

- **Disclosures:** they never hide fees, the recipient, the network or finality, though raw hashes may sit behind a details link.
- **Undo:** blockchain payments can't be undone, so a short cancellable delay before sending and the escrow refund window replace it. Real undo exists only for drafts, labels and filters.
- **Truncation:** long values are cut in the middle, and labels, errors and notifications are never cut.
- **Read-only and disabled states:** read-only content stays focusable at 4.5:1 contrast, and a disabled button says how to enable it.

**Before release, each money component meets Carbon's component checklist:**

- every state specified: hover, focus, selected, disabled, read-only, error and warning
- a documented focus order
- layouts that work down to 320 px
- strings ready for translation, decimal separators included
- amounts stored as strings or big integers
- 80% unit-test coverage
- screen-reader checks in VoiceOver and NVDA

## Screens and patterns

**Each screen names its grid and its patterns, so you and the agent share one vocabulary.** Pattern names follow [UI Patterns](https://ui-patterns.com/patterns) and Carbon.

| Screen | Grid | Patterns | Key rule |
| --- | --- | --- | --- |
| Every screen | Carbon 2x grid | Home Link, four Navigation Tabs (Spending, Statements, Refunds, Alerts), and a global header with the test-network badge | No dropdown menus or breadcrumbs, because the app is one level deep |
| Spending page | Hierarchical: spend against the limit gets the largest area and is read first | Dashboard, Fill in the Blanks limit editor, Good Defaults, Activity Stream of agent actions, Usage Meter that warns near 80% | Few metrics and one color per data set |
| Statements | Asymmetrical columns: the table takes about two-thirds and the detail panel one-third, collapsing to one column on phones | Pagination grouped by month (Archive), Table Filter, Sort By Column, Search Filters with result counts and clear-all, Progressive Disclosure for row detail, Source Citations linking each row to its transaction | Never Continuous Scrolling, and an empty state replaces an empty table |
| Escrow refunds | Column grid | Data table, Modal confirmation, Input Feedback, Inline Help Box ("What is escrow?") | Each refund deadline shows as a fixed date and time |
| Spending alerts | Column grid | Rule Builder ("spend over 5 USDC and vendor not on the allowlist"), Notifications, Settings, Morphing Controls for pausing | Pausing takes one click, resuming needs a confirmation, and alerts are never bundled or timed out |
| Spend confirmation | One column inside a modal | Preview, Structured Format for the amount and address, Permission Priming on first use, Choice Closure after confirming | Amount, recipient, network, remaining limit and maximum loss stay visible |
| Reader challenge pages | Manuscript: one column read top to bottom | Wizard, Steps Left, Inline Help Box, Copy Box for code and addresses, FAQ | Autocomplete never fills addresses or amounts |

Charts follow Carbon's data-visualization rules: bars start at zero, lines never bridge missing data, and a single series is labeled directly with no legend.

## Reader journey

**A reader goes from a module's notes to a first verified test payment in seven steps, and the plan's timer stops at the last one.**

1. **Walkthrough:** a 60-second clip in the notes shows the challenge done with worthless test money.
2. **Welcome Screen:** one button, "Make your first verified test payment."
3. **Lazy Registration:** no sign-up before the wallet.
4. **Template Gallery:** the reader opens that module's starter project, which is locked to the test network and keeps key files out of git.
5. **Permission Priming:** a plain screen explains the first signature before the wallet asks, and "Not now" gets equal weight.
6. **Playthrough:** the reader sends the test payment.
7. **Success State:** the verified transaction appears with its explorer link, and a Suggested Action proposes setting a spending limit.

**Engagement rewards learning, never spending.**

- **Levels:** the ladder's four rungs work as levels.
- **Appropriate Challenge:** difficulty rises only after mastery.
- **Achievements:** each gate awards one, and it is verified on the blockchain.
- **Progress map:** it fills only from real proofs, so the Goal-Gradient Effect never runs on fake progress.
- **Fresh Start Effect:** each new rung is a re-entry point for readers who fell behind.
- **Reminder Scheduler:** readers choose their own reminder time.

Readers never see streak counters, random rewards or leaderboards.

**The journey also covers the stages most plans forget.**

| Stage | What Ambition provides |
| --- | --- |
| Get help | Recovery steps for a stuck transaction, a wrong network and a failed signature, an FAQ, GitHub issues for bugs, and a fixed support block in every module |
| Expand | A documented path from test money to real money that keeps the same limits, confirmations and alerts, published only after an independent contract audit |
| End use | Disconnecting the wallet, revoking spending permissions, and exporting statements as CSV |

## Words

**Each money concept gets one word, defined once and used everywhere, so beginners and the agent read the same thing.**

| Term | Meaning | Never say |
| --- | --- | --- |
| Wallet | An account on the blockchain, controlled by a secret key | Account |
| Test money | Free tokens on Sui's test network with no real value | Free money |
| USDC | A digital dollar, backed one-for-one by real dollars | Coin |
| Agent | An AI program that acts on its own, such as paying for data | Bot |
| Spending limit | The most an agent may spend in a day, enforced by a contract | Budget, cap |
| Escrow | A contract that holds a payment until the service delivers or the deadline passes | Hold |
| Refund | Money that escrow returns automatically after a missed deadline | Chargeback |
| Sign | Approve a transaction with the wallet's secret key | Accept, OK |
| Final | Recorded on the blockchain and impossible to reverse | Done, complete |
| Seed phrase | The secret words that control a wallet, never to be shared | Password |

**Microcopy rules:**

- **Buttons:** they name the action and the amount, such as "Send 5 test USDC" or "Refund 2 test USDC," and never just "OK," "Submit" or "Done."
- **The way out:** it is always "Cancel," never "Decline," "No thanks" or a guilt line.
- **Test-money notice:** every money screen says "Test money on Sui testnet" until real money is allowed.
- **Errors:** they say what happened and what to do next, in words as well as color.
- **Style:** sentence case, digits for numbers, and a unit on every amount.
- **Metaphors:** each one says where it breaks, for example "escrow works like a referee holding the money, but unlike a card payment there is no chargeback."

## Maintenance and tooling

**The guidelines are maintained like code, because their main contributor is an AI agent that starts every session without memory.**

- **Releases:** numbered releases with a changelog. Renaming or removing a token is a breaking change, so products built on Ambition can pin a release and upgrade on purpose. Each part is labeled draft, preview or stable.
- **Decision log:** every approval and rejection goes into a short dated file the agent reads at the start of each session, so it never re-proposes a rejected idea. Public entries double as Build in Public material.
- **House rules:** an agent instructions file holds the principles, the persuasion policy and your approval step, and a CONTRIBUTING file holds the same rules for people. A proposal template doubles as the agent's brief and checks that Figma matches the code.
- **Automated checks:** do-and-don't pairs, contrast tests and Carbon's code audit run on every change before it reaches you, and the docs are generated from the code at each release.
- **Support:** the README publishes a best-effort response time, with a separate one for security reports.
- **Audit:** the [Design System Checklist](https://www.designsystemchecklist.com/) is run at each release.

| Tool | Setup | Note |
| --- | --- | --- |
| [Carbon MCP](https://www.carbondesignsystem.com/getting-started/carbon-mcp/overview) | Connect Claude Code to IBM's remote server and sign in with a free IBMid | Its code audit, code search and docs search tools check code against Carbon's rules. IBM logs your search text against your email domain unless you opt out, which is acceptable for public work. |
| Carbon packages | Install @carbon/react or @carbon/web-components | Set CARBON\_TELEMETRY\_DISABLED=1, because the packages report to IBM when installed otherwise |
| Figma | Start from Carbon's free community kit (v11), then set layout grids and variables from the tokens before drawing | Confirm the education account can use community kits |
| Figma MCP server | As set up in the main plan | The education plan allows 200 design-reading calls a day |

## Sources

- [Carbon Design System](https://www.carbondesignsystem.com/), including the [Carbon MCP overview](https://www.carbondesignsystem.com/getting-started/carbon-mcp/overview), [Carbon for AI](https://www.carbondesignsystem.com/building-blocks/foundations/carbon-for-ai), [2x Grid](https://www.carbondesignsystem.com/building-blocks/foundations/2x-grid), [status indicators](https://www.carbondesignsystem.com/building-blocks/core/patterns/status-indicators) and [dialogs](https://www.carbondesignsystem.com/building-blocks/core/patterns/dialogs)
- [carbon-design-system/carbon-mcp on GitHub](https://github.com/carbon-design-system/carbon-mcp), for its terms of use and telemetry
- [carbon-design-system/carbon on GitHub](https://github.com/carbon-design-system/carbon), Apache 2.0 license
- [UI Patterns: pattern library](https://ui-patterns.com/patterns)
- [Design System Checklist](https://www.designsystemchecklist.com/)
- [W3C Design Tokens Community Group: first stable version (October 28, 2025)](https://www.w3.org/community/design-tokens/2025/10/28/design-tokens-specification-reaches-first-stable-version/)
- [Brad Frost: Atomic Design](https://atomicdesign.bradfrost.com/)
- [Flux Academy: How to use a grid in web design](https://www.flux-academy.com/blog/how-to-use-a-grid-in-web-design)
- Google Visual Assets Guidelines, Part 1 (Behance, 2013), shared in this project
