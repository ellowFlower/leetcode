# 543. Diameter of Binary Tree
The implementation uses DFS and for every node calculates the diameter. A node's diameter is the sum of the depth of both children. The maximum calculated diameter is the result.
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
    int diameter = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return diameter;
    }

    private int maxDepth(TreeNode node) {
        if (node == null) {
            return 0;
        }

        var leftDepth = maxDepth(node.left);
        var rightDepth = maxDepth(node.right);
        diameter = Math.max(leftDepth+rightDepth, diameter);

        // +1 because the current node is a new depth layer
        return Math.max(leftDepth, rightDepth) + 1;
    }
}
```
