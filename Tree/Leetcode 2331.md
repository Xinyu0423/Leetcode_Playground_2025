# Soultion 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def evaluateTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        if root.left is None and root.right is None:
            if root.val == 1:
                return True
            else:
                return False
        left_node = self.evaluateTree(root.left)
        right_node = self.evaluateTree(root.right)
        if root.val == 2:
            return left_node or right_node
        elif root.val == 3:
            return left_node and right_node
```