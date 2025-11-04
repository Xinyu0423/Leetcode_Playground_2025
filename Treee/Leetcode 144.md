# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def preorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        self.res = []
        self.preorder(root)
        return self.res
    
    def preorder(self, root):
            if root is None:
                return None
            self.res.append(root.val)
            self.preorder(root.left)
            self.preorder(root.right)
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
    def preorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        stack = [root]
        res = []
        while len(stack) > 0:
            poped_element = stack.pop()
            res.append(poped_element.val)
            if poped_element.right is not None:
                stack.append(poped_element.right)
            if poped_element.left is not None:
                stack.append(poped_element.left)
        return res
```

# Solution 3
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def preorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        res = []
        stack = []
        p = root
        while len(stack) > 0 or p is not None:
            while p is not None:
                res.append(p.val)
                stack.append(p)
                p = p.left
            if len(stack) > 0:
                p = stack.pop()
                p = p.right
        return res
```