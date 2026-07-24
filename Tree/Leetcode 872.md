# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: Optional[TreeNode]
        :type root2: Optional[TreeNode]
        :rtype: bool
        """
        leaf_nodes1 = self.dfs(root1)
        leaf_nodes2 = self.dfs(root2)
        # print(leaf_nodes1)
        # print(leaf_nodes2)
        if leaf_nodes1 == leaf_nodes2:
            return True
        else:
            return False

    def dfs(self, root):
        leaf_nodes= ""
        if root is None:
            return ''
        if root.left is None and root.right is None:
            leaf_nodes +=str(root.val) + ','
        leaf_nodes += self.dfs(root.left)
        leaf_nodes += self.dfs(root.right)
        return leaf_nodes
```