# 338. Counting Bits
The idea is to count the 1 bits for a single number with the bitwise and operator and the bitwise right shift operator, and do this for all numbers 0 to n (input).

## Code
```go
func countBits(n int) []int {
    r := []int{}
    for v := range n+1 {
        c := 0
        for v != 0 {
            if v&1 == 1 {
                c++
            }
            v >>= 1
        }
        r = append(r, c)
    }
    return r
}
```
