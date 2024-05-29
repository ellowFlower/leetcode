# 235. Lowest Common Ancestor of a Binary Search Tree
The idea is that a lowest common ancestor is found if both input values have a lower depth than the lowest common ancestor.

The implementation uses BFS to go through the tree and find the result.
## Code
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        current = root
        while current:
            if q.val < current.val and p.val < current.val:
                current = current.left
            elif q.val > current.val and p.val > current.val:
                current = current.right
            else:
                return current
```
