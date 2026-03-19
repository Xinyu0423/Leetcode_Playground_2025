# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        return self.dfs(root, p, q)
        
    def dfs(self, root, p, q):
        if root is None:
            return None
        if root == p or root == q:
            return root
        left_node = self.dfs(root.left, p, q)
        right_node = self.dfs(root.right, p, q)
        if left_node is not None and right_node is not None:
            return root
        if left_node is None and right_node is not None:
            return right_node
        if left_node is not None and right_node is None:
            return left_node
        if left_node is None and right_node is None:
            return None
```