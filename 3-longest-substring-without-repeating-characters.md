# 3. Longest Substring Without Repeating Characters
The idea is to go through the array character by character and in every iteration check if it is a valid substring. If an invalid substring is found, the start of the substring is extended until a valid substring is found. 

The implementation uses a pointer `l` to mark the start of a substring and a pointer `r` to mark the end. All characters of the current substring are saved in the set `charSet`. The end of a substring is continuously extended, and the start pointer is moved if a duplicate character is found. The length of the longest substring is updated in every iteration.

## Code
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charSet = set()
        l = 0
        res = 0

        for r in range(len(s)):
            while s[r] in charSet:
                charSet.remove(s[l])
                l += 1
            charSet.add(s[r])
            res = max(res, r-l+1)

        return res
```
