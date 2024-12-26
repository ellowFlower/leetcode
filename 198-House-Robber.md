# 198. House Robber
Solve the subbproblems in reverse order and combine them.

## Code
```go
func rob(nums []int) int {
    nums = append(nums, 0)
    for i := len(nums)-3; i >= 0; i-- {
        nums[i] = max(nums[i] + nums[i+2], nums[i+1])
    }
    return max(nums[0], nums[1])
}

func max(a, b int) int {
    if a > b {
        return a
    }
    if b > a {
        return b
    }
    return a
}
```
