# 217. Contains Duplicate
While looping through the input slice, check if the value existed before.

## Code
```go
func containsDuplicate(nums []int) bool {
    visited := make(map[int]int)
    for _, n := range nums {
        if visited[n] == 1 {
            return true
        }
        visited[n] = 1
    }
    return false
}
```

