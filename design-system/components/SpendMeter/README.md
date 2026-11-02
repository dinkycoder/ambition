# SpendMeter

Spend against a daily spending limit that resets. This is the headline figure on the spending page.

**You provide:** the amount spent, the limit, the reset time, and the alert threshold (80% by default).

**Behavior:**

- The figure uses `amount-lg` with its unit.
- The bar fills in `interactive`, with a tick at the alert threshold.
- Near the limit, a warning appears in words with the triangle icon.
- It is a meter, not Carbon's progress bar, because a daily limit resets and a progress bar never decreases.

**Don't:**

- Color the bar red or green.
- Celebrate staying under the limit.
- Hide the amount left.
