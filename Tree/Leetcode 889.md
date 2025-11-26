# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def constructFromPrePost(self, preorder, postorder):
        """
        :type preorder: List[int]
        :type postorder: List[int]
        :rtype: Optional[TreeNode]
        """
        return self.createTree(preorder, 0, postorder, 0, len(preorder))
    
    def createTree(self, preorder, i, postorder, j , n):
        if n <= 0:
            return None

        root = TreeNode(preorder[i])
        if n == 1:
            return root
        
        p = j
        while preorder[i + 1] != postorder[p]:
            p += 1
        k = p - j + 1
        root.left = self.createTree(preorder, i + 1, postorder, j, k)
        root.right = self.createTree(preorder, i + k + 1, postorder, j + k, n - k -1)
        return root
```