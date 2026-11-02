# AgentProposalLabel

Marks a spend or action that the AI agent proposed, and explains why on request. It follows Carbon for AI's label-and-explanation rule.

**You provide:** the agent's stated reason in plain words, plus any figures it relied on.

**Behavior:**

- It appears on every agent-proposed item in `SpendConfirmation`, statements and alerts.
- The "Why?" toggletip opens on click or Enter, and Esc closes it.

**Don't:**

- Use it as decoration.
- Hide the reason behind hover alone.
- Imply the agent can't be wrong.
