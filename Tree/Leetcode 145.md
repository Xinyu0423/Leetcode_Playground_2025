# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def postorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        self.res = []
        self.postorder(root)
        return self.res
        
    def postorder(self, root):
        if root is None:
            return None
        self.postorder(root.left)
        self.postorder(root.right)
        self.res.append(root.val)
```