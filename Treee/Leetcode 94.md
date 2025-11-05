# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        self.res = []
        self.inorder(root)
        return self.res
    
    def inorder(self, root):
        if root == None:
            return None
        self.inorder(root.left)
        self.res.append(root.val)
        self.inorder(root.right)
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
    def inorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        res = []
        stack = []
        while len(stack) > 0 or root is not None:
            while root is not None:
                stack.append(root)
                root = root.left
            poped_element = stack.pop()
            res.append(poped_element.val)
            root = poped_element.right
        return res
```