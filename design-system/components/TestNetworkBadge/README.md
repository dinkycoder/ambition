# TestNetworkBadge

Marks test money on every screen, so nobody mistakes a practice payment for a real one.

**You provide:** the network name.

**Behavior:**

- It sits in the global header on every screen and in every `SpendConfirmation`.
- It uses `network-test`, the only place that color appears.
- The words "Test money" always appear, never the icon alone.

**Don't:**

- Hide it on small screens.
- Reuse its color for anything else.
