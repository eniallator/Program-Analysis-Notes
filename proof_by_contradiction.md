# Proof By Contradiction

- Take some proposition
- Take the opposite of the proposition
- Try proving the opposite is true

## Proving Truth

- Proving something is true can be hard
- We need to prove that a proposition is always true

## Counter Example

- All letter boxes are red
- I am a letter box, therefore I am red
- p → q
- So the reverse is true
- "I am red, therefore I am a letter box"?
- Well, no, I could be a red ferrari

## Contradiction

- A contradiction in logic is a statement is always false
- E.g p and ~p
- Can interpret easily with a truth table

| p   | ~p  | p and ~p |
| --- | --- | -------- |
| 1   | 0   | 0        |
| 0   | 1   | 0        |

## An Easy Example

- Tim guys 2 shirts for just over £60. Prove that at least one of the shirts cost more than £30
- if x + y > 60,
  - Then either x > 30 or y > 30

---

- Assume the counter proposition
- That neither shirt costs more than £30
  - x < 30
  - y < 30
  - x + y < 60
- This leads to a contradiction
  - x + y > 60
  - x + y < 60
- So the counter proposition must be false
- One of the shirts costs more than £30

## More ambitious Example

- Show that `√2` is an irrational number
- That is, a number that can't be written down as a simple fraction

---

- Adopt the counter proposition, that `√2` is rational
- If it was, we could write
  - `√2 = a/b` a fraction in it's lowest form where `a` and `b` are integers and at least one of them is an odd number
- `√2 = a/b`
- `2 = a²/b²`
- `a² = 2b²`
- by this, `a²` must be even
  - Since `a²` has a factor of `2`
- The square of an odd number is off, and that would tell us that `a` must be even and `b` must be odd for `a/b` to be a fraction in it's lowest form
- So we conclude:
  - `a` is even and `b` is odd
- But if `a` is even, then `a²` must be even
- And `a²` would be a multiple of `4`
- If `a²` is a multiple of `4`, and `a² = 2b²` So dividing `2` on both sides, `b² = multiple of 2` so b is also even

---

- We have a contradiction:
  - `a` is even and `b` is odd
  - `a` is even and `b` is even
- So the counter proposition is false
- And `√2` must be irrational

## Cracking Enigma

- During `WW2` (critically the battle of the Atlantic), Nazi Germany used Enigma machines for secure communication
- TL;DR Turing came a long and whipped out his computer
