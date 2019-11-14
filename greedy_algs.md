# Greedy ALgorithms

- One amongst different strategies to solving problems
  - Greedy method
  - Dynamic programming
  - Network flow

## Five Representative Problems

- Interval strategies
- Weighted interval scheduling
- Bipartite matching
- Independent set

## Interval Scheduling Problem

- A bunch of tasks
- Looks like a gantt chart
- Specified
  - Two intervals are compatible if they don't overlap
  - **Input:** A set of intervals where each interval has a start and an end time
  - **Output:** The largest selection of compatible intervals that can be made

### Greedy Approach

- Make a series of locally best choices
- Very efficient way to solve problems
- Be greedy when you can get away with it
- Can't always get away with it
- Some problems not amenable to a greedy approach

---

- Have a set of choices that are entirely local
- May end up with an optimal solution
- Algorithm:
  - Go through the time slots one by one
  - If there's a choice to make, choose the best one
- Better strategy
  - Choose interval with earliest possible end point
  - Make a priority queue based on the end times
  - Then create a set of compatible intervals over the queue
  - Check compatibility for the current interval by comparing the last item in the set
- Running time of above alg
  - Priority queue:
    - Build once `O(n)`
    - Remove items n times `O(nlogn)`
  - Tight bound?
    - No - what if all intervals end at the same time?
    - Then it's linear

### Weighted Interval Scheduling

- Each interval has a weight
- Could be a measure of how important it is that the interval is scheduled
- Specified
  - **Input:** Set of intervals with start/finish times plus weights
  - **Output:** Subset of compatible intervals with the greatest total weight
- Cannot be solved with a greedy approach
  - Better with a divide and conquer approach

## Bipartite Matching

- **Input:** A graph that is bipartite (definition later)
- **Output:** Matching with the most edges possible
- Can also be scaled to any graph as well

## P NP

- NP space problems are a set of algorithms that exponentially grow out of control
- P space problems are even harder than NP problems compare difficulty in verifying that solution is even valid
  - May not even be feasible to prove that a solution is valid

## Shortest Path Problem

- Least weighted path to get to a destination
- Vertices added to a set A once their distance from s established
- For vertices v not yet in A we keep track of the total distance travelled - the vertices already in the route

### Djikstra's Algorithm

- Works on weighted graphs
- Has the same traversal logic as a breadth first search, except it's modified to be a priority queue instead of a queue
- The priorities are the total weights so far and can be modified if a shorter route has been found
