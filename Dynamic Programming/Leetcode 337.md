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
        left = self.dfs(root.left)
        right = self.dfs(root.right)
        rob = root.val + left[0] + right[0]
        not_rob = max(left[0], left[1]) + max(right[0], right[1])
        return [not_rob ,rob]

        
```