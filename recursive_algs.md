# Recursive Algorithms

## Running Time

- `T(n)` can be expressed as recurrence
  - `T(n) = T(n - 1) + cn`
  - `T(1) = c`
- 1 recursive call on problem with one less value `+`
- `θ(n)` recursive steps

### Recursive Analysis Example

```text
T(n) = T(n - 1) + c₁n
T(1) = c₂
```

- Find expression for `T(n - 1)`

```text
T(n - 1) = T((n - 1) - 1) + c₁(n - 1)
T(n - 1) = T(n - 2) + c₁(n - 1)
```

- Then put that exp. into the original equation

```text
T(n) = T(n - 2) + c₁(n - 1) + c₁n
T(n) = T(n - 2) + c₁n - c₁ + c₁n
T(n) = T(n - 2) + 2c₁n - c₁
```

- Repeat until pattern is found

```text
T(n - 2) = T((n - 2) - 1) + c₁(n - 2)
T(n - 2) = T(n - 3) + c₁(n - 2)
```

- And put it in the original ...

```text
T(n) = T(n - 3) + c₁(n - 2) + 2c₁n - c₁
T(n) = T(n - 3) + c₁n - 2c₁ + 2c₁n - c₁
T(n) = T(n - 3) + 3c₁n - 3c₁
```

- And another one ...

```text
T(n - 3) = T((n - 3) - 1) + c₁(n - 3)
T(n - 3) = T(n - 4) + c₁(n - 3)
```

- You know the deal by now 😉

```text
T(n) = T(n - 4) + c₁(n - 3) + 3c₁n - 3c₁
T(n) = T(n - 4) + c₁n - 3c₁ + 3c₁n - 3c₁
T(n) = T(n - 4) + 4c₁n - 6c₁
```

- The stages of `T(n)`

```text
T(n) = T(n - 1) + 1c₁n - 0c₁
T(n) = T(n - 2) + 2c₁n - 1c₁
T(n) = T(n - 3) + 3c₁n - 3c₁
T(n) = T(n - 4) + 4c₁n - 6c₁
T(n) = T(n - 5) + 5c₁n - 10c₁
```

- The equation:

```text
T(n) = T(n - k) + kc₁n - (k * (k + 1) / 2)c₁
```

- Considering the base case so `k` is `n - 1` with the base case as `T(1) = c₂`

```text
T(n) = T(n - k) + kc₁n - (k * (k + 1) / 2)c₁
T(n) = T(n - (n - 1)) + (n - 1)c₁n - ((n - 1) * ((n - 1) + 1) / 2)c₁
T(n) = T(1) + (c₁n² - c₁n) - ((n - 1) * n / 2)c₁
T(n) = c₂ + c₁n² - c₁n - ((n² - n) / 2)c₁
T(n) = c₂ + c₁n² - c₁n - ½n²c₁ + ½nc₁
T(n) = c₂ + ½n²c₁ - ½nc₁
```

- So this example has a running time complexity of `θ(n²)`
