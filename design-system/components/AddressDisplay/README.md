# AddressDisplay

Shows a wallet address so a person can check it: split into groups of four, with the first and last groups emphasized.

**You provide:** the full address, plus the saved name if there is one.

**Behavior:**

- **Short form.** Shows the saved name and the first and last groups, joined by an ellipsis. Truncation always cuts the middle.
- **Full form.** Shows every group in `code`. Screen readers read it group by group.
- **Copy.** Copies the full value. The confirmation message stays put and focus does not move.
- **Checksum.** Shows "Checksum valid" with a check icon, or an error in words.

**Do:**

- Prefer saved names over raw addresses (Recognition over Recall).
- Show the full address on request.

**Don't:**

- Auto-complete an address.
- Hide the last group.
- Show an address without a way to see it in full.
