# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def goodNodes(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        return self.dfs(root, root.val)
    
    def dfs(self, root, largest_value):
        if root is None:
            return 0
        res = 0
        if root.val >= largest_value:
            res = 1
            largest_value = root.val
        res += self.dfs(root.left, largest_value)
        res += self.dfs(root.right, largest_value)
        return res
```