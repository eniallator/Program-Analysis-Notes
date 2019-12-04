# Coursework 2 Notes

## Network Flow

- How things move from node `s` to node `t`
- If there's a fixed amount in `s`, it will go to `t` taking the

### Flow Graph

- Shows the actual flow (capacity)
- E.g an edge from V1 to V2 with a capacity of 100, can easily handle a capacity of 30

### Residual Graph

- Residual forwards
  - Forward edge
- Capacity to redirect (factual flow)
  - Backwards edge
- E.g an edge connecting V1 and V2
  - From V1 to V2 has a capacity of 70
  - From V2 to V1 has a capacity of 30
- Can show this with 2 separate edges
- Or can show this with 70 with a right arrow above the number and then 30 with a left arrow above it

### Simple Paths

- Find a path from `s` to `t` and the lowest capacity edge is the bottleneck edge
- Basically, watch last thursday's lecture recording

## Call Stack Diagram

- e.g on a method called `product`

```text
30 🡑                  🡓 call
    product({2, 3, 5})
  6 🡑               🡓 Call
     product({2, 3})
   2 🡑           🡓 Call
      product({2})
```
