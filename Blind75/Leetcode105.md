# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        n = len(preorder)
        root = self.createTree(preorder, inorder, 0, 0, n)
        return root

    def createTree(self, preorder, inorder, i, j, n):
        if n == 0:
            return None
        root = TreeNode(preorder[i])
        k = j
        while inorder[k] != root.val:
            k += 1
        left_size = k - j
        right_size = n - left_size -1
        left_node = self.createTree(preorder, inorder, i + 1, j ,left_size)
        right_node = self.createTree(preorder, inorder, i + 1 + left_size, k + 1, right_size)
        root.left = left_node
        root.right = right_node
        return root        
```