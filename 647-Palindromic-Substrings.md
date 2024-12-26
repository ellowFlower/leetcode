# 647. Palindromic Substrings
The underlying subproblem is checking if a string is a palindrome. This can be repeated for all substrings.

## Code
```go
func countSubstrings(s string) int {
    res := 0
    for i := range s {
        // odd length palindromes
        l, r := i, i
        for l >= 0 && r <= len(s)-1 && s[l] == s[r] {
            res++
            l--
            r++
        }
        // even length palindromes
        l = i
        r = i+1
        for l >= 0 && r <= len(s)-1 && s[l] == s[r] {
            res++
            l--
            r++
        }
    }
    return res
}
```
