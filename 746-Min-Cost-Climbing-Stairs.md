# 746. Min Cost Climbing Stairs
Solve all subproblems in reverse order and combine them.

## Code
```go
func minCostClimbingStairs(cost []int) int {
    cost = append(cost, 0)
    for i := len(cost)-3; i >= 0; i-- {
        cost[i] = min(cost[i] + cost[i+1], cost[i] + cost[i+2])
    }
    return min(cost[0], cost[1])
}

func min(a, b int) int {
    if a < b {
        return a
    }
    if b < a {
        return b
    }
    return a
}
```
