# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        if root is None:
            return True
        return self.checker(root.left, root.right)
        
        
    def checker(self, left_node, right_node):
        if left_node is None and right_node is None:
            return True
        if left_node is None and right_node is not None:
            return False
        if left_node is not None and right_node is None:
            return False
        if left_node.val != right_node.val:
            return False
        return self.checker(left_node.left, right_node.right) and self.checker(left_node.right, right_node.left)
```

# Solution 2
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        if root is None:
            return True
        from collections import deque
        queue = deque()
        queue.append([root, root])
        while queue:
            left_node, right_node = queue.popleft()
            if left_node is None and right_node is None:
                continue
            if left_node is not None and right_node is None:
                return False
            if left_node is None and right_node is not None:
                return False
            if left_node.val != right_node.val:
                return False
            queue.append([left_node.left, right_node.right])
            queue.append([left_node.right, right_node.left])
        return True
```