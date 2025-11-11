# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def findTilt(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        self.res = 0
        self.sum_root(root)
        return self.res
        
    def sum_root(self, root):
        if root == None:
            return 0
        left_sum = self.sum_root(root.left)
        right_sum = self.sum_root(root.right)
        self.res += abs(left_sum - right_sum)
        return left_sum + right_sum + root.val       
```