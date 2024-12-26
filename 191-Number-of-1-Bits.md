# 191. Number of 1 Bits
We always check the last bit of n until all bits are checked.

## Code
```go
func hammingWeight(n int) int {
    r := 0
    for n != 0 {
        // check if last bit of n is a 1
        // can also be done as: r += n % 2
		if n&1 == 1 {
			r++
		}
        // shift n by one to be able to check the next bit in the next loop round
        n >>= 1
    }
    return r
}
```
