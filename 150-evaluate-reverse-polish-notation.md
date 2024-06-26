# 150. Evaluate Reverse Polish Notation
The idea is to always apply an operator to the last two elements before the operator.

The implementation uses a stack pushing the numbers of the input string onto it. When an operator occurs in the input, it is applyied to the two most recent elements of the stack. The result is again pushed onto the stack. At the the stack contains only one element which is the result of the whole expression.

## Code
```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        
        for t in tokens:
            if t == "+":
                stack.append(stack.pop() + stack.pop())
            elif t == "-":
                x, y = stack.pop(), stack.pop()
                stack.append(y-x)
            elif t == "*":
                stack.append(stack.pop() * stack.pop())   
            elif t == "/":
                x, y = stack.pop(), stack.pop()
                stack.append(int(y/x))
            else:
                stack.append(int(t))
            

        return stack.pop()
```
```java
class Solution {
    public int evalRPN(String[] tokens) {
        var stack = new ArrayDeque<Integer>();
        int x, y;
 
        for (String t: tokens) {
            switch(t) {
                case "+":
                    stack.push(stack.pop() + stack.pop());
                    break;
                case "-":
                    x = stack.pop();
                    y = stack.pop();
                    stack.push(y-x);
                    break;
                case "*":
                    stack.push(stack.pop() * stack.pop());
                    break;
                case "/":
                    x = stack.pop();
                    y = stack.pop();
                    stack.push(y/x);
                    break;
                default:
                    stack.push(Integer.valueOf(t));
            }
        }

        return stack.pop();
    }
}
```
