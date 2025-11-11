# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSubtree(self, root, subRoot):
        """
        :type root: Optional[TreeNode]
        :type subRoot: Optional[TreeNode]
        :rtype: bool
        """
        if root == None:
            return False
        if self.same(root, subRoot):
            return True
        elif self.isSubtree(root.left, subRoot):
            return True
        elif self.isSubtree(root.right, subRoot):
            return True
        else:
            return False
    
    def same(self, root, subRoot):
        if root == None and subRoot == None:
            return True
        if root == None or subRoot == None:
            return False
        if root.val != subRoot.val:
            return False
        return self.same(root.left, subRoot.left) and self.same(root.right, subRoot.right)
```

# Soultion 2
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSubtree(self, root, subRoot):
        """
        :type root: Optional[TreeNode]
        :type subRoot: Optional[TreeNode]
        :rtype: bool
        """
        preroot = self.preorder(root)
        preSubRoot= self.preorder(subRoot)
        i = preroot.find(preSubRoot)
        if i != -1 and (i == 0 or preroot[i - 1] == "#" or preroot[i - 1] == ','):
            return True
        else:
            return False

    def preorder(self, root):
        pres = ''
        if root == None:
            pres = '#'
        else:
            pres += str(root.val) + ','
            pres += self.preorder(root.left)
            pres += self.preorder(root.right)
        return pres
```