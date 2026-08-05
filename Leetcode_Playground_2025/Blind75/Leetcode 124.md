# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        self.pathSum = float('-inf')
        self.max_Gain(root)
        return self.pathSum
    
    def max_Gain(self, node):
        if node is None:
            return 0
        left_gain = max(0, self.max_Gain(node.left))
        right_gain = max(0, self.max_Gain(node.right))
        self.pathSum =max(self.pathSum, node.val + left_gain + right_gain)
        return node.val + max(left_gain, right_gain)
```