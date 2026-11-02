# SpendConfirmation

The dialog shown before any step that spends, approves or signs, so the person knows exactly what will happen to their money.

**You provide:**

- the action and the amount, which become both the title and the primary button label ("Send 5 test USDC")
- the recipient's saved name and full address
- the network
- the spending limit left after this payment
- the most the person could lose
- an `AgentProposalLabel` when the agent proposed the spend

**Behavior:**

- **Placement and focus.** Cancel sits on the left and receives first focus, overriding Carbon's danger-modal default. Esc always cancels.
- **The summary stays visible.** The amount, recipient, network and finality line never move behind "Show more".
- **Guarding against double sends.** After the person presses Send, the button shows Carbon's inline loading and stays disabled until the payment is final or has failed, so a second click can't send twice.

**Do:**

- Use it for every spend, approval and signature, including on the first payment.
- Show amounts with their unit in tabular figures.

**Don't:**

- Pre-fill the amount.
- Pre-select a choice.
- Style Cancel as a weaker link.
- Add urgency of any kind.
