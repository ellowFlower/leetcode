# 424. Longest Repeating Character Replacement
The idea is to go through the input array character by character and in every step check if it is still a valid substring, meaning only one char is used with `k` amount of exceptions. If it is not a valid substring the first character of the substring is removed. Keeping track of the longest substring is done by a counter.

The implementation uses a pointer `l` to represent the start of a substring and `r` to represent the end. In the dictionary `charCount` the values of a substring with its coresponding frequency is saved. If a invalid substring is found, the pointer `l` is incremented until the substring is valid. 



## Code
```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        l, result = 0, 0
        charCount = defaultdict(int)

        for r in range(len(s)):
            charCount[s[r]] = charCount[s[r]] + 1
            while (r-l+1) - max(charCount.values()) > k:
                # invalid substring
                charCount[s[l]] -= 1
                l += 1
            result = max(result, r-l+1)

        return result
```
