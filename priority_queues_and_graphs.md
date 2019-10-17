# Priority Queues And Graphs

## Priority Queue

- An ordered sequence of elements
- A linear data structure
- `a₁` is the first element in the queue
- `a`<sub>`n`</sub> is the last element in the queue

### Priorities

- ORdering of elements is determined by the priority associated with each element
- `a₁` has as high a priority as any element in `a₁, ..., a`<sub>`n`</sub>
- Priorities do not need to be unique
  - Provide partial ordering of the elements

### Issues

- How might priorities be determined?
- What operations are typically performed on priority queues?
- How can priority queues be efficiently implemented?
  - 2 possible implementations being looked at
    - Unsorted list
    - Heap

### Unsorted List Implementation

- Adding a new element:
  - Add to the end
  - Takes `O(1)`
- Removing front of queue
  - Requires linear search of queue
  - Takes `O(n)` in worst case
- Updating priority of element
  - No reordering of elements required
  - Takes `O(1)` assuming constant time access to priority values
- Need to figure out which operation is performed most, so we can figure out the tight bound

### Binary Heap Implementation

- Array of values constrained in a particular way
- [SEE HERE FOR NOTES](https://github.com/eniallator/Data-Structures-and-Algorithms-Notes/tree/master/BinaryHeaps)
- In the mean time, you can browse reddit/watch some youtube/check social media

### Top 10 Anime Crossovers

<img width=100 src="dab.gif">

| Operation       | Unsorted List | Binary Heap                |
| --------------- | ------------- | -------------------------- |
| Removal         | `θ(1)`        | `θ(1)`, `O(log₂n)`, `Ω(1)` |
| Insertion       | `θ(1)`        | `θ(1)`, `O(log₂n)`, `Ω(1)` |
| Change priority | `θ(1)`        | `O(log₂n)`, `Ω(1)`         |

### Bottom Up Heap

- Used when constructing a heap from a collection of input values
- Put the bottom row in place without doing any comparisons
- Then continue constructing the heap from the bottom up, maintaining the heap order property

#### MATHS TIME 😱

- For each node, processing time for node of height `h`
  - `O(h)`
- Number of nodes of height `h`
  - `<= ceil(n / (2`<sup>`h + 1`</sup>`))`
- Total running time
  - `O(n)`
