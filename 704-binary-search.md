# 704. Binary Search
The idea is to split the search space in half for every iteration.

The implementation uses a left and right pointer to indicate the search space. In every iteration of the while loop it splits the search space in half.
## Code
```java
class Solution {
    public int search(int[] nums, int target) {
        var l = 0;
        var r = nums.length - 1;
        int m;

        while (l <= r) {
            m = (l + r) / 2;
            if (nums[m] == target) {
                return m;
            } else if (target < nums[m]) {
                r = m - 1;
            } else {
                l = m + 1;
            }
        }

        return -1;
    }
}
```
