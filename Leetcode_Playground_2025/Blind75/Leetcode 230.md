# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        self.tree_vals = []
        self.in_order(root)
        return self.tree_vals[k -1]
    def in_order(self, root):
        if root is None:
            return None
        self.in_order(root.left)
        self.tree_vals.append(root.val)
        self.in_order(root.right)
        
```