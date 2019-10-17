# Stable Match

## Issues

- Is the algorithm guaranteed to terminate?
- How efficient is it?
- Can we be certain that the algorithm always finds a stable match?
  - How can we prove these?
- How fair is the algorithm?
- Does it matter how we resolve the non-determinism?

## Termination

- Need some measure of progress
  - A value that monotonically increases as number of executions of loop increases
    - Monotonically increasing - as it progresses, it shouldn't ever go down, it can flat-line however (AKA gradient >= 0)
    - There's also monotonically decreasing
- Consider: the number of blue people that are still free
  - Reject: this doesn't necessarily decrease each time the loop is executed
- Consider: the number of engaged couples
  - Reject: this doesn't necessarily decrease each time the loop is executed

## Measure Of Progress

- The number of proposals made so far
- Always increases by 1 when loop executed
- Upper limit on number of proposals is `n`<sup>`2`</sup>
  - When `n` is the number of blue people ( and number of red people)
- Gives upper limit on the progress

## Efficiency

- Running time will depend on how long it takes for each execution of loop
  - Different implementations have different running times
- Possible to do it in constant time
- Need more detailed consideration of data structures

## Proving Correctness

- A stable match is always found
- Let's show that it would be a contradiction to assert that ...
- _There is an unstable pair in a match produced by the algorithm_
- A proof by contradiction
- ~~Brute force?~~
  - Much easier to get a counter example to show it's not true

## Proof Of Correctness

- Suppose we have the following
  - An unstable pair `α` and `β`
  - `α` paired by the algorithm with `β'` ≠ `β`
  - `β` paired by the algorithm with `α'` ≠ `α`
- Instability means
  - `α` prefers `β` to `β'`
  - `β` prefers `α` to `α'`
- Case 1: `α` didn't propose to `β` at any point
  - `α` proposes in decreasing order of preference
  - `α` must have proposed to `β'`
  - So `β'` must be preferred to `β` by `α`
  - Contradicts previous assumption
- Case 2: `β` proposed to `α` but was rejected (immediately or at a later point)
  - `β` would only reject `α` of a blue person they preferred
  - so `α'` must be preferred to `α` by `β`
  - Contradicts previous assumption
