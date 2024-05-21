# 110. Balanced Binary Tree
The implementation executes DFS recursively and calculates for every node if it is balanced and the maximum depth. The maximum depth is used to indicate if the parent node is balanced. If all nodes are balanced the result is true otherwise false.
## Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isBalanced(TreeNode root) {
        var result = dfs(root);
        return result.getKey();
    }

    // returns (isBalanced, depth)
    private Pair<Boolean, Integer> dfs(TreeNode root) {
        if (root == null) {
            return new Pair<Boolean, Integer>(true, 0);
        }

        var left = dfs(root.left);
        var right = dfs(root.right);
        var balanced = left.getKey() && right.getKey() && Math.abs(left.getValue() - right.getValue()) <= 1;
        return new Pair<Boolean, Integer>(balanced, Math.max(left.getValue(), right.getValue()) + 1);
    }
}
```
