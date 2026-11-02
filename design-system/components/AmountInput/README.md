# AmountInput

A text field for an amount of money, with its unit and up to six decimals.

**You provide:** the label, the unit (USDC), the current value as a string, and any limit the value must stay under.

**Behavior:**

- It is a text input, not Carbon's number input, because arrow-key steppers can nudge an amount by accident.
- It accepts digits and one decimal point only.
- It never guesses: "5" and "0.5" are never reinterpreted.
- It shows its value back in `SpendConfirmation` before anything is sent.
- Its errors appear in words and in color.

**Do:**

- Store the value as a string or a big integer, never as a floating-point number.
- Show the unit beside the field, every time.

**Don't:**

- Pre-fill an amount.
- Add plus and minus buttons.
- Accept free-form text such as "five".
