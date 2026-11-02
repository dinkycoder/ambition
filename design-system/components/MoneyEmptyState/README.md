# MoneyEmptyState

Replaces an empty table or figure, and says which of three cases applies.

**You provide:** the case (no data, no results or error), a title, one sentence, and one action.

**Behavior:**

- **No data:** offers the first step.
- **No results:** offers to clear filters.
- **Error:** says the read failed and that money hasn't moved, and offers a retry.

**Don't:**

- Show "$0" or "0 transactions" when a read failed. That would misstate a balance.
- Leave a dead end with no action.
