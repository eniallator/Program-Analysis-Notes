# Network Flow

- How things move from node `s` to node `t`

## Flow Graph

- Shows the actual flow (capacity)
- E.g an edge from V1 to V2 with a capacity of 100, can easily handle a capacity of 30

## Residual Graph

- Residual forwards
  - Forward edge
- Capacity to redirect (factual flow)
  - Backwards edge
- E.g an edge connecting V1 and V2
  - From V1 to V2 has a capacity of 70
  - From V2 to V1 has a capacity of 30
- Can show this with 2 separate edges
- Or can show this with 70 with a right arrow above the number and then 30 with a left arrow above it

## Augment

- If following a forwards edge, add the value to the backwards edge, if following a backwards edge, subtract from the backwards edge

## Implementation

- Finding a `s` to `t` path in the residual graph
  - Perform a DFS from `s`
  - Takes `O(n + m)` time
  - `O(m)` since we assume all vertices have at least one incident edge

## Cuts In A Network

- Let's fucking cut the shit out of out network
- Basically cut the network in half
- Mathsy notation:
- Let G = (V, E) be some network
- (A, B) is a cut in the network if:
  - s is in A
  - t is in B
  - A union B = V and A intersection B = {}
  - In other words (A, B) is a partition of the set V
- Many different possible cuts
- The cut capacity is the total capacity of the edges that were removed
- The cut capacity is useful because the minimum cut capacity that can be found is the maximum flow that the sink can handle

## Bipartite Matching As Network Flow

- May have a problem like the bipartite graph from earlier in the year
- For the residual graph, there's a residual forwards capacity of 1 and backwards actual flow of 0, aka (1, 0)
- When augmenting a single path, turn all the edges (0, 1)
- Then find another simple path, however can't go down the other paths
- Basically bipartite matching for it
