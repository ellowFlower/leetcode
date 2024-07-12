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

```go
func isValid(s string) bool {
	var stack []rune
	brackets := map[rune]rune{
		'(': ')',
		'{': '}',
		'[': ']',
	}

	for _, v := range s {
		if _, ok := brackets[v]; ok {
			stack = append(stack, v)
			continue
		}

		if len(stack) == 0 || brackets[stack[len(stack)-1]] != v {
			return false
		}

		stack = stack[:len(stack)-1]
	}

	return len(stack) == 0
}

```
