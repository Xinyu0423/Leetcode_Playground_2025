# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: Optional[TreeNode]
        """
        return self.createTree(preorder, 0, inorder, 0, len(preorder))

    def createTree(self, pre, i, ins, j, n):
        if n <= 0:
            return None
        root = TreeNode(pre[i])
        p = j
        while ins[p] != pre[i]:
            p += 1
        k = p - j
        root.left = self.createTree(pre, i + 1, ins, j, k)
        root.right = self.createTree(pre, i + k + 1, ins, p + 1, n - k - 1)
        return root
```