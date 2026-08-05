# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def convertBST(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        self.val_sum = 0
        self.traverse(root)
        return root

    def traverse(self, root):
        if root is None:
            return
        self.traverse(root.right)
        self.val_sum += root.val
        root.val = self.val_sum
        self.traverse(root.left)
```