# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def mergeTrees(self, root1, root2):
        """
        :type root1: Optional[TreeNode]
        :type root2: Optional[TreeNode]
        :rtype: Optional[TreeNode]
        """
        if root1 is None and root2 is None:
            return None
        if root1 is None and root2 is not None:
            return root2
        if root1 is not None and root2 is None:
            return root1
        from collections import deque
        queue = deque()
        queue.append([root1, root2])
        last_root1 = root1
        last_root2 = root2
        temp_root1 = None
        temp_root2 = None
        root1.val = root1.val + root2.val
        while queue:
            popped_root1, popped_root2 = queue.popleft()
            if popped_root1.left is not None and popped_root2.left is not None:
                popped_root1.left.val = popped_root1.left.val + popped_root2.left.val
                queue.append([popped_root1.left, popped_root2.left])
            if popped_root1.left is None and popped_root2.left is not None:
                popped_root1.left = popped_root2.left
            
            if popped_root1.right is not None and popped_root2.right is not None:
                popped_root1.right.val = popped_root1.right.val + popped_root2.right.val
                queue.append([popped_root1.right, popped_root2.right])
            if popped_root1.right is None and popped_root2.right is not None:
                popped_root1.right = popped_root2.right
        return root1
            


```