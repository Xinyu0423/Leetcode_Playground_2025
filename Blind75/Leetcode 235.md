# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        path_p = self.find_path(root, p)
        path_q = self.find_path(root, q)
        ancestor = None
        for node_p in path_p:
            for node_q in path_q:
                if node_p == node_q:
                    ancestor = node_p
        return ancestor

    def find_path(self, root, node):
        path = []
        while node != root:
            path.append(root)
            if root.val > node.val:
                root = root.left
            else:
                root = root.right
        path.append(root)
        return path
```