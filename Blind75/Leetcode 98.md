# Solution
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        self.tree_vals = []
        self.in_order(root)
        if self.tree_vals == sorted(self.tree_vals) and len(list(set(self.tree_vals))) == len(self.tree_vals):
            return True
        return False
    
    def in_order(self, root):
        if root is None:
            return None
        
        self.in_order(root.left)
        self.tree_vals.append(root.val)
        self.in_order(root.right)
```