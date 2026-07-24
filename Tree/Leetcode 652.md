# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def findDuplicateSubtrees(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[Optional[TreeNode]]
        """
        self.subTrees = {}
        self.res = []
        self.seralizeTree(root)
        return self.res
    
    def seralizeTree(self, root):
        pres = ""
        if root is None:
            return "#"
        pres += str(root.val) + ','
        pres += self.seralizeTree(root.left)
        pres += self.seralizeTree(root.right)

        if pres in self.subTrees:
            if self.subTrees[pres] == 1:
                self.res.append(root)
            self.subTrees[pres] += 1
        else:
            self.subTrees[pres] = 1
        return pres
```