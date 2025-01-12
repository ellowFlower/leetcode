# 190. Reverse Bits - Explanation

## Code
```go
func reverseBits(num uint32) uint32 {
    var res uint32 = 0
    // go through every single bit in input n
    for i := range(32) {
        // get the ith lowest bit of input n
        bit := (num >> i) & 1
        // put bit in output (start with largest bit and end with lowest)
        res = res | (bit << (31-i)) 
    }
    return res
}

// binary input to reverse 1010
// i = 0
// bit = 0
// res = 0000
// i = 1
// bit = 1
// res = 0100
// i = 2
// bit = 0
// res = 0100
// i = 3
// bit = 1
// res = 0101
```
