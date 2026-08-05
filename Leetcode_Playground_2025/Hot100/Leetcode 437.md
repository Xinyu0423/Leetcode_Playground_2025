# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> int:
        if root is None:
            return 0
        res = self.rootSum(root, targetSum)
        res += self.pathSum(root.left, targetSum)
        res += self.pathSum(root.right, targetSum)
        return res
    
    def rootSum(self, p, targetSum):
        if p is None:
            return 0
        res = 0
        if p.val == targetSum:
            res += 1
        res += self.rootSum(p.left, targetSum - p.val)
        res += self.rootSum(p.right, targetSum - p.val)
        return res
```