# 213. House Robber II
Use subproblem from House Robber I, and translate new constraint to code. We basically nest the subproblems now.

## Code
```go
func rob(nums []int) int {
    if len(nums) == 1 {
        return nums[0]
    }
    return max(robSub(nums[1:]), robSub(nums[:len(nums)-1]))
}

func robSub(nums []int) int {
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
