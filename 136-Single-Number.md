# 136. Single Number
XOR bit manipulation is used to make time and space performant. The trick is that if XORing the values only the single value will be left over.

## Code
```go
func singleNumber(nums []int) int {
    r := 0
    for _, v := range nums {
        r = v ^ r
    }
    return r
}
```
