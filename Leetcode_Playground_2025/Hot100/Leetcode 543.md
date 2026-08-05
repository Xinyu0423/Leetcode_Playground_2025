# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.res = 0
        self.dfs(root)
        return self.res
    
    def dfs(self, root):
        if root is None:
            return 0
        left_depth = self.dfs(root.left)
        right_depth = self.dfs(root.right)
        self.res = max(self.res, left_depth + right_depth)
        return max(left_depth, right_depth) + 1
```