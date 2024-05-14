# 20. Valid Parentheses
The idea is to check if every opening bracket has a matching closing bracket and they are closed in the correct order.

The implementation loops through the characters in the input string, and puts all opening brackets on a stack. If the input string is valid, it is possible to pop the correct opening bracket for every related closing bracket. In the end, an empty stack ensures that for every opening there was a closing bracket. Using a stack makes sure that always the last opened bracket is closed.

## Code
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        pairs = {
            ")": "(",
            "}": "{",
            "]": "["
        }

        for c in s:
            if c in pairs.values():
                stack.append(c)
            elif c in pairs:
                if stack == [] or stack[-1] != pairs[c]:
                    return False                
                stack.pop()

        return stack == []
```
