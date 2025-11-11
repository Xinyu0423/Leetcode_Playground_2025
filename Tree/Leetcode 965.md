# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isUnivalTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        stack = [root]
        res = []
        while len(stack) > 0:
            poped_element = stack.pop()
            if len(res) > 0 and res[-1] != poped_element.val:
                return False
            res.append(poped_element.val)  
            if poped_element.left is not None:
                stack.append(poped_element.left)
            if poped_element.right is not None:
                stack.append(poped_element.right)
        return True
```