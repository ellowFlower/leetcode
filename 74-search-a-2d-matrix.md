# 74. Search a 2D Matrix
The idea is to apply binary search twice. Once to find the correct row, and once to find the target element inside that row.

The implementation uses a left (`l`) and right (`r`) pointer to represent the search space. It starts with the whole input matrix, and after the first while loop it marks one row.
## Code
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        // find correct row
        int l = 0;
        int r = matrix.length - 1;
        int m = 0;
        while (l <= r) {
            m = (l + r) / 2;
            if (target < matrix[m][0]) {
                r = m - 1;
            } else  if (target > matrix[m][matrix[m].length-1]) {
                l = m + 1;
            } else {
                break;
            }
        } 

        // find target inside row
        l = 0;
        r = matrix[m].length-1;
        int fixRow = m;
        while (l <= r) {
            m = (l + r) / 2;
            if (target < matrix[fixRow][m]) {
                r = m - 1;
            } else  if (target > matrix[fixRow][m]) {
                l = m + 1;
            } else {
                return true;
            }
        } 

        return false;
    }
}
```
