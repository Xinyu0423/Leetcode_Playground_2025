# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rob(self, root: Optional[TreeNode]) -> int:
        return max(self.dfs(root))
    
    def dfs(self, root):
        if root is None:
            return [0, 0]
        left_val = self.dfs(root.left)
        right_val = self.dfs(root.right)
        rob = root.val + left_val[0] + right_val[0]
        not_rob = max(left_val[0], left_val[1]) + max(right_val[0], right_val[1])
        return [not_rob, rob]

```