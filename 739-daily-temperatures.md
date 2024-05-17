# 739. Daily Temperatures
The idea is to go through the input temperatures and for every value find the next value which is a larger number.

The implementation uses a stack to save the values (temperature) and the index of the values from the input array. Every element from the input is put onto the stack once and removed if the result for it is found. A result for a specific element is found when the first larger element is reached.

## Code
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        var result = new int[temperatures.length];
        var stack = new ArrayDeque<Pair<Integer, Integer>>(); // (index, value)

        for (int i = 0; i < temperatures.length; i++) {
            while (stack.size() != 0 && temperatures[i] > stack.peek().getValue()) {
                var p = stack.pop();
                result[p.getKey()] = i - p.getKey();
            }
            stack.addFirst(new Pair(i, temperatures[i]));
        }

        return result;
    }
}
```
