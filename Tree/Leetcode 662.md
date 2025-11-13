# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def widthOfBinaryTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if root is None:
            return 0
        self.first = []
        self.last = []
        max_width = 0
        self.preorder(root, 0 , 0)
        for i in range(len(self.first)):
            width = self.last[i] - self.first[i] + 1
            # print(max_width)
            # print(width)
            max_width = max(max_width, width)
        return max_width
        
    def preorder(self, root, number, height):
        if root is None:
            return None
        if len(self.first) == height:
            self.first.append(number)
        if len(self.last) == height:
            self.last.append(number)
        else:
            self.last[height] = number
        self.preorder(root.left, 2 * number + 1, height + 1)
        self.preorder(root.right, 2 * number + 2, height + 1)
```