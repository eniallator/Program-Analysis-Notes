# Notes

## Meta Notes

- The library has books
- Kingsley is JOKES LAD

## Wtf is This Module

- Look at many different types of algorithms
- Understand how to analyse them
- Assessment:
  - 2 pieces of coursework
  - Unseen exam
- Keep up with the material 👀
- VERY MATHSY

## Stable Match Problem

- Will illustrate some key concepts
  - What is a problem?
  - What is an algorithm?
  - What is a measure of progress?
  - How do we analyse an algorithm's running time?
  - How do we prove that an algorithm is correct?

### Problem to Consider

- Matching people up

```text
A     W

B     X
   ?
C     Y

D     Z
```

- This is actually a very general problem
- Can we think of some examples of how something like this could be used?
  - Buyers and sellers
  - Advertisements

---

- Perfect match
  - Everyone is paired with exactly one person

---

- People have preferences
- (Imagine the following tables are filled up randomly)

|     | 1st | 2nd | 3rd | 4th |
| --- | --- | --- | --- | --- |
| A   |     |     |     |     |
| B   |     |     |     |     |
| C   |     |     |     |     |
| D   |     |     |     |     |

|     | 1st | 2nd | 3rd | 4th |
| --- | --- | --- | --- | --- |
| W   |     |     |     |     |
| X   |     |     |     |     |
| Y   |     |     |     |     |
| Z   |     |     |     |     |

- The idea is to have as little instabilities as possible to make a stable configuration
- An instability is when 1 node is connected to one node when it's better for it to be connected to another node

### Questions

- Can a stable matching always be found?
  - Doubt it
- How can we construct a stable match when one exists?
- **Stable Match Problem**
- Applies to other situations
  - Hospital beds to patients
  - Employers and applicants

## What A Problem Is And What It Isn't

- What a problem is
  - Specification of a relationship between inputs and outputs
  - Usually a mapping - one valid output for a given input
- What a problem isn't
  - A matter of doing something in a particular way
  - Procedural
- Stable match problem is generic

## What An Algorithm Is And Isn't

- What an algorithm is
  - Specification as to how to tackle a problem
  - Can be abstracted
  - We will use informal pseudo-code language
- What an algorithm isn't
  - Not the same as a program
    - Programs implement algorithms
  - Same algorithm implemented in different languages
- Solving a problem means getting valid output for each input given to the algorithm
