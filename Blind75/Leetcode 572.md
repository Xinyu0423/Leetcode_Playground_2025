# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        serialed_root = self.pre_order(root)
        serialed_subRoot = self.pre_order(subRoot)
        print(serialed_root)
        print(serialed_subRoot)
        if serialed_subRoot in serialed_root:
            return True
        return False
    
    def pre_order(self, root):
        pres = ""
        if root is None:
            return "None,"
        pres += ',' + str(root.val) + ','
        pres += self.pre_order(root.left)
        pres += self.pre_order(root.right)
        return pres
```

# Solution 2
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if root is None:
            return False
        if self.isIdentical(root, subRoot):
            return True
        return  self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
    
    def isIdentical(self, root, subRoot):
        if root is None and subRoot is None:
            return True
        if root is None or subRoot is None:
            return False
        if root.val != subRoot.val:
            return False
        return self.isIdentical(root.left, subRoot.left) and self.isIdentical(root.right, subRoot.right)
```