# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def flatten(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        self.pre_order_vals = []
        self.preorder(root)
        res = root
        for i in range(1, len(self.pre_order_vals)):
            root.right = TreeNode(self.pre_order_vals[i])
            root.left = None
            root= root.right
        return res
    
    def preorder(self, root):
        if root is None:
            return None
        self.pre_order_vals.append(root.val)
        self.preorder(root.left)
        self.preorder(root.right)
        
```