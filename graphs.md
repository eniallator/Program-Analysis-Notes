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
- The traversal will find out a minimal traversal for the edges needed to visit each node

#### Revised Traversals

- do a traversal from every node in the graph if the node hasn't already been discovered

#### Running Time Of Traversals

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
- This means that there are `O(m)` iterations of the loop
  - Since the traversal will produce a tree

## Topological Sorting

### Working With Dependencies

- Directed graphs often encode dependencies
- Can only sort directed acyclic graphs

### Topological Sorting Of DAGs

- Topological sorting algorithms start off by associating each vertex with a number - it's `indegree`
  - The indegree is the number of edges pointing towards any given vertex
- Starts off with a stack containing all vertices with indegrees of 0
- Then goes over the out going edges to the next vertices and push them on the vertices stack
- It also decrements the indegrees of each vertex it finds by 1
- Then add the vertices with a value of 0 to the stack and repeat
- What about a queue?
  - Doesn't matter since it will be used to hold the schedulable vertices and so it will return a correct result

### Running Time

- Must be `θ(m + n)`
  - To traverse all adjacency lists

### Prioritising

- Use a priority queue instead of a stack and potentially use weights on edges
