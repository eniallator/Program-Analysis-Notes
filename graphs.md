# Graphy Bois

- General purpose data structure
  - Doesn't have to be a linear list
  - Doesn't have to be a hierarchical tree
- A graph can have components that aren't connected
  - A component must be connected in a graph
- [MY NOTES FOR GRAPHS MATEYS](https://github.com/eniallator/Data-Structures-and-Algorithms-Notes/tree/master/Graphs)
- [MY NOTES FOR TREE MATEYS](https://github.com/eniallator/Data-Structures-and-Algorithms-Notes/tree/master/Trees)

## Representing Graphs

- Adjacency matrix is very inefficient for low order connectivity since it will scale with `n²` where `n` is the number of nodes
  - `θ(1)` lookup
  - `θ(n)` to check for adjacent nodes
    - Even if there aren't any adjacent nodes, it takes `θ(n)` to find this out
- Adjacency list is good for low connectivity or smaller graphs
  - "ArrayList of ArrayLists" for Java
  - Much more space efficient
  - `θ(1)` to see each adjacent node
  - `O(n)` to see if an edge is in a graph

## Edges

- How few edges can there be?
  - Can be 0
  - If connected, then `>= n - 1`
- How many edges
  - If complete, then `n(n - 1)/2` which is `θ(n²)`
- In general, the edge set is `O(n²)`

## Algorithms

### Visiting Every Node In A Graph

- Non-linear and non-hierarchical
- Breadth/depth first traversal?
- Breadth first **TRAVERSAL**
  - Uses a queue data structure for the nodes waiting to be visited
  - Can only discover nodes in a single component
- Depth first **TRAVERSAL**
  - Uses a stack data structure for the nodes waiting to be visited

#### Revised BFT

- do a BF traversal from every node in the graph if the node hasn't already been discovered

#### Running Time Of BFT

- Measure progress?
  - Need to consider num edges/nodes
  - Increases by 1 for an iteration of the while loop
  - `n` iterations of the loop
  - Time spent per iteration?
  - Depends on num edges per node
- Number of steps within loop is `θ(1, outdegree(V))`
- `outdegree(v)` is num outgoing edges from v
- `m` total edges
- Total across all iterations of loop
- `sum(max(1, outdegree(v))) = θ(n + m)`
