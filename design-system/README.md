# Agency Lab Design System

The style guide, tokens and money components for Agency Lab. It mirrors the editable Design System artifact; the PDF is in [docs/pdf](../docs/pdf/Agency%20Lab%20Design%20System.pdf). Open any `components/<Name>/preview.html` in a browser to see a component, and add `data-theme="dark"` or `data-theme="high-contrast"` to its `<html>` tag to switch themes.

Agency Lab helps AI builders give their agents money safely, one small win at a time. It is an open-source Micro Research and Education Platform (MREP) for agentic commerce, on AWS and Base, built in public one module at a time, and an MSAIE capstone. The interface is calm, exact and honest: it shows what will happen to money before anything happens, and it never pressures anyone. Its structure follows Carbon, IBM's open-source design system, with Agency Lab's own look.

## Principles

1. **Consent before money moves.** Nothing spends, approves or signs without a confirmation that shows the amount, the recipient, the network and the fact that the payment is final. Build it with `SpendConfirmation`.
2. **Truth over polish.** Every amount links to its blockchain record. A failed read shows as a failure (`MoneyEmptyState`, error), never as $0.
3. **Safe by default.** Limits start low, alerts start on, nothing is pre-approved, and amounts and recipients start empty.
4. **Plain words.** One term per concept, defined at first use.
5. **Usable by everyone.** Text meets 4.5:1 contrast in every theme (7:1 in `high-contrast`), everything works by keyboard and screen reader, and color is never the only signal.

## Voice and words

Write like a careful friend who knows blockchains: short sentences, plain words, no hype, no exclamation marks, no emoji. Use "you" for the reader and "your agent" for their AI agent. Use sentence case everywhere ("Send 5 test USDC", not "Send 5 Test USDC").

- **Name the action and the amount on every money button.** Write "Send 5 test USDC" or "Refund 2 test USDC", never "OK", "Submit" or "Done".
- **The way out is always "Cancel".** Never "Decline", "No thanks" or a guilt line.
- **Say test money until real money is allowed.** Every money screen carries `TestNetworkBadge` and the words "Test money on Base Sepolia".
- **Errors say what happened and what to do next**, in words as well as color: "The blockchain didn't respond. Your money hasn't moved. Try again."
- **Metaphors say where they break**: "Escrow works like a referee holding the money, but unlike a card payment there is no chargeback."

Use these words and only these:

| Say | Meaning | Never say |
| --- | --- | --- |
| wallet | An account on the blockchain, controlled by a secret key | account |
| test money | Free tokens on Base Sepolia with no real value | free money |
| USDC | A digital dollar, backed one-for-one by real dollars | coin |
| agent | An AI program that acts on its own, such as paying for data | bot |
| spending limit | The most an agent may spend in a day, enforced by a contract | budget, cap |
| escrow | A contract that holds a payment until the service delivers or the deadline passes | hold |
| refund | Money escrow returns automatically after a missed deadline | chargeback |
| sign | Approve a transaction with the wallet's secret key | accept, OK |
| final | Recorded on the blockchain and impossible to reverse | done, complete |
| seed phrase | The secret words that control a wallet, never to be shared | password |

**Persuasion policy.** Learning content may use curiosity, progress through levels and verified achievements. Money screens may use only what aids understanding (grouping, steps, saved names, diagrams) while the amount, recipient, finality and Cancel stay visible. Scarcity, countdowns, streak counters, decoy choices, preset amounts, pre-selected choices, loss framing and sunk-cost appeals are banned everywhere. Before adding any new technique, ask whether users would still agree if they saw exactly how and why it was presented.

## Color

Colors are semantic roles with three themes: `light` (the default), `dark` and `high-contrast`. The theme is chosen by the user and switches while the app runs. Never write a raw color; use a token.

- **Surfaces.** Set pages on `background`, cards, panels and dialogs on `layer`, and table headers and zebra rows on `layer-alt`. Put `overlay-scrim` behind dialogs only.
- **Text.** Set body text and amounts in `text-primary`, and helper text, timestamps and metadata in `text-secondary`. `text-disabled` is for disabled labels only.
- **Action.** `interactive` is the one action color: primary buttons, links (`link`) and selected states. Put `text-on-interactive` on its fill, and use `interactive-hover` for hover and press.
- **Edges and focus.** Give every control an edge in `border-strong`, and use `border-subtle` only for decorative dividers. Keyboard focus is a 2px solid `focus` ring with a 2px offset, on every interactive element.
- **Status colors mean status and nothing else.**
  - `support-success` (teal): final payments and passed checks.
  - `support-warning` (ochre): near-limit and new-address warnings.
  - `support-danger` (vermilion): failed payments and errors.
  - `support-info` (blue): submitted and confirming payments.

  Each one appears with its icon and a word, and its `-soft` tint goes behind notices. Success is teal rather than green, so it never depends on telling red from green.
- **Brand.** `brand-ink` and `brand-tint` are brand surfaces for the cover, the docs header and highlighted tips. Never use them for status, and never use status colors in the brand.
- **Test network.** `network-test` with `text-on-network-test` marks test money and is used only by `TestNetworkBadge`.
- **Charts.** Draw a single series in `interactive`. For several series, use tints of `interactive` and `brand-ink`, never status colors. Bars start at zero, and lines never bridge missing data.

## Type

There are two system font stacks, `font-sans` and `font-mono`, so pages load instantly. A brand display face may come later, for brand pieces only.

- Use `display` once per page at most, `heading-01` for page titles, `heading-02` for sections and `heading-03` for dialog and card titles.
- Use `body` as the default app text, `body-lg` for explanations in reader challenges, `label` for field labels, table headers and tags, and `helper` under fields.
- Set money in `amount-lg` (the one headline figure on the spending page) or `amount`, always with tabular figures (`font-variant-numeric: tabular-nums`) and always with a unit: "5.000000 USDC".
- Set wallet addresses and transaction hashes in `code`, in groups of four (`0x71C7 656E … 976F`), with the first and last groups in `text-primary` and the middle in `text-secondary`.
- Line heights sit on the 4px unit.

## Space, grid and shape

- **Spacing.** Every gap is a spacing token on the 4px unit: `space-4` between an icon and its label, `space-8` inside tags, `space-12` for field padding, `space-16` for card padding on phones, `space-24` for dialog padding on desktop, and `space-32` and up between sections. `space-2` is for hairlines only.
- **Grid.** Layouts follow Carbon's 2x grid at `bp-sm` (4 columns), `bp-md` (8) and `bp-lg` and up (16), with 16px padding. Modules 9–12 need two layouts only: phone (`bp-sm`) and desktop (`bp-lg`). Set the grid before drawing.
- **Grid types.** The spending page is hierarchical, with spend against the limit given the largest area. Statements use asymmetric columns, about two-thirds table and one-third detail panel. Reader challenges use a single manuscript column.
- **Shape and depth.**
  - Corners: `radius-sm` for inputs, `radius-md` for buttons, cards and dialogs, `radius-lg` for large panels, and `radius-pill` for status tags and badges only.
  - Shadow: `shadow-overlay` appears on dialogs and menus only. Dark mode separates surfaces with `layer`, and `high-contrast` separates them with `border-strong`.
- **Sizes.** Controls are `control-md` tall (40px). Primary actions on phones are `control-lg` (48px), which is also the minimum touch target.

## Motion

Motion explains a change in money; it never decorates.

- **Durations and easing.** Use `duration-fast-01` (70ms) for presses, `duration-moderate-01` (150ms) for status changes and `duration-moderate-02` (240ms) for dialogs, with `easing-standard`, `easing-entrance` or `easing-exit`.
- **One cue per payment state.** Submitted fades in, confirming shows a slow pulse on its icon, and final, failed and refunded swap their icon once.
- **Reduced motion.** Under `prefers-reduced-motion`, everything changes instantly.
- **Banned.** Nothing loops, bounces or celebrates a payment.

## Iconography

- **Icon set.** Use the open-source Lucide set at `icon-16`, `icon-20` and `icon-24`, as outline strokes in the text color of their context.
- **Spoken names.** Give every icon the name a screen reader speaks. An icon-only button needs a visible tooltip and an accessible label.
- **Reserved icons.** These keep one meaning each, and no other icon may resemble them:
  - check-circle means final or verified
  - send means spend
  - undo-2 means refund
  - flask-conical means test network
  - triangle-alert means warning
  - x-circle means failed
- **Small sizes.** Icons at 16px are drawn for that size, not shrunk.
- **No logo yet.** Agency Lab has no mark yet, so set the name in `heading-03` in `text-primary`. Never borrow IBM or Google marks, pictograms or palettes.

## Components

General components come from Carbon (`@carbon/react` or `@carbon/web-components`, with `CARBON_TELEMETRY_DISABLED=1`), styled through these tokens. These include buttons, text inputs, dropdowns, toggles, the data table, notifications, the modal, inline loading, tags, toggletips, tabs, the content switcher, pagination, search and the date picker. Don't use Carbon's number input or progress bar for money: their arrow keys can nudge an amount, and the bar cannot reset.

Agency Lab adds the money components Carbon lacks:

- `SpendConfirmation`: the dialog before any spend, approval or signature.
- `AmountInput`: a text field for amounts with unit and six decimals.
- `AddressDisplay`: a wallet address in groups of four, with a checksum check and a copy button.
- `TransactionStatus`: submitted, confirming, final, failed and refunded, each with its own shape, icon and word.
- `SpendMeter`: spend against a daily limit that resets.
- `LimitEditor`: the limit written as a sentence.
- `TestNetworkBadge`: test money marked on every screen.
- `DeadlineDisplay`: a fixed date and time, never a ticking timer.
- `MoneyEmptyState`: no data, no results and error, never showing $0 for a failed read.
- `AgentProposalLabel`: marks a spend the agent proposed and explains why.

Never let a money message disappear on a timer. Failures and spending alerts stay until dismissed.
