# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: Optional[TreeNode]
        """
        return self.createTree(inorder, 0 , postorder, 0, len(inorder))
        
    def createTree(self, ins, i, post, j, n):
        if n <= 0:
            return None
        root = TreeNode(post[n + j - 1])
        p = i
        while ins[p] != post[n + j - 1]:
            p += 1
        k = p - i
        root.left = self.createTree(ins, i, post, j, k)
        root.right = self.createTree(ins, p + 1, post, j + k, n - k - 1)
        return root
```