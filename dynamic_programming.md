# Dynamic Programming

## Reflecting On Divide And Conquer

- The promise of divide and conquer
  - Many problems naturally decompose into sub-problems
  - Sub-problems have the same form as original problem
  - Recursive solutions appear to solve the problem elegantly
- Problem: sometimes there's redundancy
  - Same sub-problems instances re-occur frequently
  - Inefficient to repeatedly solve the same problem
- MEMO STUFF 😃

### Example: Syntactic Parsing

- Checking valid syntax
- Suppose that you need to check that a string is syntactically valid
- Rules specify when a string is well formed
- Various possible scenarios
  - Checking syntax of a program
  - Analsing syntax of a natural language expression
- AKA a parser

---

- Rules
  - The string has to be an `S` phrase
  - An `S` phrase is an `S₁` phrase followed by an `S₂` phrase
  - An `S₁` phrase is an `A` phrase followed by a `B` phrase
  - An `S₂` phrase is a `C` phrase followed by a `D` phrase

---

- If `ABCD` were designated parts of an array and you were to generate all permutations to see if they are valid, there would be multiple permutations with the exact same parts mapped to `ABCD`

## Dynamic Programming Approach

- Only solve each sub-problem once
  - Start by solving small problems and remember solutions
  - Using solutions to small sub-problems, solve slightly bigger problems
  - Systematically solve entire space of sub-problems, remembering solutions
  - Eventually the original problem will be solved

## Weighted Interval Scheduling Problem

- Decomposing the problem
  - To find the solution at time 10, you need to have the solutions to every time before that as well
- Once a solution has been found, if a new interval has been added, then using the old solution, you can probably find a new valid solution
- Go through the time scheduling alg like so:
- Just deal with it 😎

| Time | Intervals        | Weight |
| ---- | ---------------- | ------ |
| 0    | {}               | 0      |
| 1    | {α₁}             | 3      |
| 2    | {α₂}             | 6      |
| 3    | {α₁, α₃}         | 8      |
| 4    | {α₁, α₃}         | 8      |
| 5    | {α₁, α₃}         | 8      |
| 6    | {α₂, α₄}         | 13     |
| 7    | {α₁, α₃, α₅}     | 17     |
| 8    | {α₁, α₃, α₅}     | 17     |
| 9    | {α₁, α₃, α₅, α₆} | 18     |
| 10   | {α₁, α₈}         | 26     |

- At every timestep, you not only look at the previous solution, but every single one before that as well
- Perfect for dynamic programming, since you can keep a memo of all solutions before that

---

- My thoughts
  - Keep an array for the best solution at each time interval where you index the array with the desired time interval
  - Pass the array to the function when doing recursion
  - L I N E A R <sub><sub>ah fuck that's too meta</sub></sub>
- Keep a 2D array where you keep track of the current best solution, where you consider the value of what I was thinking above, then also the previous current best as well

### Matrix algorithm

- Make a matrix of the number of intervals by the weights,
- At interval 0, the weights are all 0
- As you process more and more intervals, the matrix will fill up

## Sequence Alignment

- TL;DR seeing how similar two sequences are to each other
  - The extent in which one sequence needs to be edited to produce another
  - Penalty for gaps
  - Penalty for differences
- Measure the distance between two strings which is the amount of changes you need to do to one to make it into the other

## The Problem

- An alignment `M` of `X` and `Y` is a set of pairs `(i,j)` where
  - `1 <= i <= n` and `1 <= j <= m`
  - For each `i` there is at most one pair `(i,j)` in `M`
  - For each `j` there is at most one pair `(i,j)` in `N`
  - `(i,j)` is in `M`, `(i',j')` is in `M` and `i < i'` implies `j < j'`
- Note that:
  - No pairings cross over
  - The number of pairs in `M` can be at most `min(n,m)`
    - i.e. `|M| <= min(n,m)`
  - The number of unpaired positions `gap(M) = max(n,m) - |M|`
- For each `i`, `j` the optimal solution `B(i,j)` is the best among:
  - `delta(xi, yi) + B(i - 1, j - 1)`
  - `gamma + B(i - 1, j)`
  - `gamma + B(i, j - 1)`

```text
sequenceAlignment(X,Y):
  let B(i, 0) <- i * gamma for each 1 <= i <= n
  let B(0, j) <- j * gamma for each 1 <= j <= m
  for i <- 1 to n
    for j <- 1 to m
      B(i, j) <- min[
        delta(xi, yj) + B(i - 1, j - 1),
        gamma + B(i, j - 1),
        gamma + B(i - 1, j)
      ]
```

- Tight bound
  - θ(mn)
- `B()` is a matrix containing the cost of going from one char to another
- E.g (where the costs are arbitrary)

|     | a   | b   | c   |
| --- | --- | --- | --- |
| a   | 0   | 8   | 5   |
| b   | 8   | 0   | 7   |
| c   | 5   | 5   | 0   |

- Then Make a matrix for the two sequences where you figure out each cost (where gaps cost 5)

|     | 0   | a   | b   | c   |
| --- | --- | --- | --- | --- |
| 0   | 0   | 5   | 10  | 15  |
| b   | 5   | 8   | 5   | 10  |
| a   | 10  | 5   | 10  | 10  |
| b   | 15  | 10  | 5   | 10  |
| c   | 20  | 15  | 10  | 5   |

- Then starting from the top left of the table, traverse to the bottom right, following the smallest costs and getting the cheapest path

## Djikstra's With Negative Weights

- NOT IMPOSSIBLE
- Can do with d y n a m i c \_ p r o g r a m m i n g

```javascript
BellmanFord(G, w, s, t):
  let B(0, t) <- 0
  let B(0, t) <- infinity for each v in V - {t}
  for i <- 1 to n - 1 // n vertices
    for each v in V // Vertices
      B(i, v) <- B(i - 1, v)
      for each (v, u) in E // Edges from v
        B(i, v) <- min[
          B(i, v),
          w(v, u) + B(i - 1, u)
        ]
```

- Work from the destination and get to the start
- `B()` is a matrix
- Time complexities:
  - `O(n³)`
  - `Ω(n²)`
