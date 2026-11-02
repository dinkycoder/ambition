# DeadlineDisplay

Shows a deadline, such as an escrow refund window, as a fixed date and time with its time zone.

**You provide:** the deadline as an ISO timestamp, plus the person's time zone.

**Behavior:**

- It is plain text in a `time` element.
- After the deadline, it states what happened and when.

**Don't:**

- Use a ticking countdown, seconds or urgency colors. A deadline is a fact, not pressure.
