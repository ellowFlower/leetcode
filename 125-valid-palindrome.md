# 125. Valid Palindrome
The solution should not use the python string reverse function. 

A string is a palindrome if there is no difference when reading from left to right or right to left. The string can also be seen as a character array. The implementation uses two pointers to compare the characters starting from the left and right side. If the pointers meet in the middle of the string, all characters are the same and the string is a palindrome. As only aphanumeric characters are relevant, all other ones are skipped.

## Code
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s)-1
        while l < r:
            while l < r and not s[l].isalnum():
                l += 1
            while r > l and not s[r].isalnum():
                r -= 1
            if s[l].lower() != s[r].lower():
                print(s[l] + " : " + s[r])
                return False
            l += 1
            r-= 1
        return True
```
