# Huffman Codes

- Compression algorithms use this
- Lossless
- We don't give a shit about a lot of the information

---

- Message sent using an alphabet of characters
- How efficiently can messages involving these chars be encoded in binary?

## Straight Forward Encoding

- Suppose we are using an alphabet `A` containing 64 characters
  - 26 upper and also lowercase
  - Space, tab, newline
  - Punctuation
  - Round/square brackets
- Each character `c` in `A` can be encoded using a distinct 6 bits
- We refer the encoding of `c` as `gamma(c)`

| c   | gamma(c) |
| --- | -------- |
| a   | 000000   |
| b   | 000001   |
| c   | 000010   |
| d   | 000011   |
| ... | ...      |

- Sending `n` characters requires `6n` bits
- Exactly 6 bits per character
- But this does not exploit differences in character frequencies
  - E.g `e` is much more frequent than `x`
- Encoding should depend on how frequent a character is

### Character Probabilities

- Associate a probability `p(c)` with each character `c`
- `p(c)` is the probability that a randomly selected character will be `c`
- Probabilities for all characters in alphabet must total 1

### Variable Length Encoding

- Common characters take up less space than less used characters
- Average less space
- Morse code uses this sort of concept
- Want to minimise number of bits per letter
- The weighted average of character encoding length
  - Weight is the probability of each character

### Prefix

- Morse code uses a longer space in between each character
- No encoding should be a prefix of any other
- Decoding can be done without needing to mark the end of the character

#### Eager Left To Right

- As soon as a sequence of bits is found as a sequence of bits from some `gamma(c)`, decode the string as `c`
- Consider the remaining bit string starting with the next bit

#### Prefix Code Trees

- Make a tree where the leaf nodes are the characters and the branches are either 0 or 1
