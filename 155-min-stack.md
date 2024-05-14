# 155. Min Stack
The idea is to save for every value in the stack the corresponding minimum value of the whole stack. 

## Code
```python
class MinStack:
    def __init__(self):
        self.stack = [] # (value, min value)

    def push(self, val: int) -> None:
        minimum = val if self.stack == [] else min(val, self.getMin())
        self.stack.append((val, minimum))

    def pop(self) -> None:
        self.stack.pop()

    def top(self) -> int:
        return self.stack[-1][0]

    def getMin(self) -> int:
        return self.stack[-1][1]
```
