# 567. Permutation in String
Validating if a string is a permutation of another one can be done by checking if both strings consist of the same characters. This is done for every substring inside the input string `s2`.

The implementation uses a two pointers `l, r` to loop through every substring of the string `s2` which has the same length as string `s1`. For every substring it checks if the substring is a permutation of `s1`.


## Code
```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        l, r = 0, len(s1)-1
        while r < len(s2):
            s2Substring = s2[l:r+1]
            for c in s1:
                if c in s2Substring:
                    s2Substring = s2Substring.replace(c, '', 1)
            if not s2Substring:
                return True
            l += 1
            r += 1
        return False
```
