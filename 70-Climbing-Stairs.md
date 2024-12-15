## 70. Climbing Stairs
It is the fibonacci problem. Solve all subproblems backwards to get the solution. Can also be done recursively.

## Code
```go
func climbStairs(n int) int {
    a, b := 1, 1

    for ;n > 1; n-- {
        t := a
        a = a + b
        b = t
    }

    return a
}
```
