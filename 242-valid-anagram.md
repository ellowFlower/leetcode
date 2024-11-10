# 242. Valid Anagram
Check if s contains all letters of t.

## Code
```go
func isAnagram(s string, t string) bool {
    if len(s) != len(t) {
        return false
    }

    letters := make(map[rune]int)    
    for _,v := range s {
        letters[v] = letters[v] + 1
    }

    for _,v := range t {
        if letters[v] > 0 {
            letters[v] = letters[v] - 1
        }
        if letters[v] == 0 {
            delete(letters, v)
        }
    }

    return len(letters) == 0
}
```
