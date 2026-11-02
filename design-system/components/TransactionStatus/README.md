# TransactionStatus

The state of a payment, which always shows color, a distinct shape or icon, and a word together.

**You provide:** one of five states, plus a link to the transaction record.

| State | Meaning | Token | Icon |
| --- | --- | --- | --- |
| Submitted | Sent to the network, not yet recorded | `support-info` | open circle |
| Confirming | Recorded in a block, not yet final | `support-info`, dashed edge | half-filled circle |
| Final | Recorded and irreversible | `support-success` on `support-success-soft` | check-circle |
| Failed | Rejected; no money moved | `support-danger` on `support-danger-soft` | x-circle |
| Refunded | Returned by escrow | `text-secondary` | undo-2 |

**Behavior:**

- "Sent" and "final" are never the same state, so a person never pays twice thinking the first payment was lost.
- Each change is announced to screen readers.

**Don't:**

- Show a status by color alone.
- Animate it beyond one icon swap.
