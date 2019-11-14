# MSTs

- Take some graph structure with a weight function
- Find a subset of edges so that it would remain that you could still reach every single node
- Kruskal algorithm gives a minimum spanning tree

## Another MST Algorithm

- Discovered by Jarnik first
  - Rediscovered by Prim
  - Rediscovered (again) by Dijkstra
  - Commonly known as Prim's algorithm

### Jarnik

- Grows the tree `E'` from an arbitrary starting point
- As `E'` grows, it spans an increasing number of the vertices
- `E'` grows by one each iteration
- Selects the edge that's the closest vertex to the tree produced so far
- Committing to this edge is safe because the cut property

#### The closest Vertex

- Consider graph G = (V,E)
- Suppose the algorithm has so far selected the set of edges `E'`
- `E'` spans the vertices S where S is a subset or equal to V
- In other words, `G' = (S, E')` is a spanning tree

#### Maintaining Distance

- Record distance of v from (S, E′) as value δ(v)
- As E′ grows δ(v) may reduce
- Also useful to record identify of the vertex u ∈ S where δ(v) = w(v, u)
  - Refer to this value as β(v)

#### Jarnik's Algorithm

```text
select some vertex s ∈ V  and let δ(s) = 0
initialise E′ to be the set {}
for all v ∈ V − {s} let δ(v) = ∞
for all v ∈ V  let β(v) = ⊥
let Q be a priority queue containing elements of V
while |E′| < |V| − 1
  remove u from front of priority queue Q
  if β(u) != ⊥ then      (% i.e.  u is not s)
    add {u, v} to E′ where β(u) = v
  for each {u, x} ∈ E where x remains in Q
    if δ(x) > w(u, x) then
      let δ(x) = w(u, x)
      let β(x) = u
return E′
```

#### Run-time

- Construction of a priority queue
- Continuously going through the priority queue
- Updates to the delta/beta values will have a limit of the number of edges in the graph
  - upper bound is `O(m)`
- It also uses a priority queue
  - Continuously popping nodes off
  - Rebuilding takes `O(logn)` time
  - Total running time for algorithm is `O(mlogn)`
- For a lower bound, the graph itself must be it's own minimal spanning tree
  - So `m = n - 1`
  - Then there's no reordering of the priority queue, so the `logn` disappears
  - lower bound is `Ω(n)`
