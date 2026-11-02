# LimitEditor

Sets a spending limit as a sentence people can read aloud: "Let [agent] spend [5] USDC per [day]."

**You provide:** the agents, the allowed periods, and the current limit.

**Behavior:**

- The amount field follows the `AmountInput` rules.
- Lowering a limit is instant.
- Raising one opens a `SpendConfirmation`-style dialog that states the new maximum.
- New agents start at a low default limit, which comes from Good Defaults.

**Don't:**

- Pre-fill a high limit.
- Save a raised limit in place without confirmation.
