# Analysing Algorithm Efficiency

- Things we might want to know
  - How efficient is a given algorithm?
  - What sized problems can be solved within a reasonable time?
  - Is some new algorithm really more efficient than the existing one?
  - Which of two possible algorithms is best for my particular use case?
- We'll always look at ways to answer questions like these
- Measure running time of an algorithm through experimentation
  - Implement algorithm
  - Choose appropriate inputs
  - Run program on all inputs
  - Plot results
  - Determine rate at which time increases as input grows
- Can have significant advantages:
  - Can give very realistic impression of actual time
  - Can be useful when comparing two candidate algorithms
  - Subtle differences in running time may emerge
  - Useful when software, hardware and possible blah blah blah slide went off screen
- Variety of potential problems
  - Can be time consuming to implement algorithms effectively
  - Can be time consuming to run on larger inputs
  - Etc.

## Asymptotic analysis

- Look at how running time increases as time grows
  - A rough classification of the rate of growth
  - Concerned with the very long term growth rate
- Running time as a function
  - Problem size is `n`
  - Running time of algorithm is referred to `t(n)`
  - `t(n)` is the number of steps that an input of size `n` takes

## Asymptotic Bounds

- Asymptotic analysis of efficiency involves determining **bounds**
  - Upper bound `O(.)`
    - `O(.)` that is the worst case
    - Formal definition: `t(n)` is `O(f(n))` if there are constants `n₀` and `c > 0` such that `t(n)` < `c * f(n)` for all `n > n₀`
  - Lower bound `Ω(.)`
    - `O(.)` that is the best case
  - Tight bound `θ(.)`
    - `O(.)` that is the average case
    - Not always a thing
    - Only applicable when the upper and lower bound belong to the same complexity class
- Always care about the functions with really big numbers, so it doesn't matter what the lines do initially

### Example

- Linear searching
  - Best case is where the item is at the front of the list
    - `θ(1)`
  - Inputs where the target value isn't in the list
    - `O(n)`
  - Expected performance - avg case
    - Don't know what the distribution of values/inputs is
    - Probabilities of each possible input might not form a uniform distribution

### Lower Bound For A Problem

- What is the lower limit on how efficiently a problem can be solved?
  - No particular algorithm in mind
  - This is a property of a **problem**, not an **algorithm**
  - Can be a very hard question to answer
  - Requires generalising across all possible algorithms
- E.g lower bound for the sorting problem
  - Know that we can sort in `O(nlogn)` time
    - C.f merge sort
  - Possible for quicker sorting?
  - Only consider swapping sorting algorithms
  - Comparison sort decision tree
    - The number of sort configurations of the outcome will be `n!`
    - Height will at least be `log(n!)`
    - `n!` has at least `n/2` terms that are at least `n/2`
      - E.g if `n = 3`, `n! = 6`
      - `n/2 = 1.5` and there are 2 terms `> 1.5`
    - So `log n! >= log(n/2 ^ (n/2))`
    - `log(n/2 ^ (n/2)) = n/2 log n/2`
    - `n/2 log n/2` is `O(n log n)`
    - Lower bound for comparison-based sorting is `O(n log n)`

### Upper Bound?

- Can't have an upper bound for a problem since there's effectively an infinite number of upper bounds
  - Not useful!

### How Useful Are Upper/Lower Bounds

- Does it make sense to specify upper/lower bounds?
