# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def longestUnivaluePath(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        self.res = 0
        self.findPath(root)
        return self.res

    def findPath(self,root):
        if root is None:
            return 0
        left_depth = self.findPath(root.left)
        right_depth = self.findPath(root.right)
        left = 0
        right = 0
        if root.left and root.val == root.left.val:
            left = left_depth + 1
        else:
            left = 0
        if root.right and root.val == root.right.val:
            right = right_depth + 1
        else:
            right = 0
        self.res = max(left + right, self.res)
        return max(left, right)
```