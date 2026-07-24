# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def averageOfLevels(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[float]
        """
        res = []
        queue = [root]
        while queue:
            n = len(queue)
            temp = []
            for _ in range(n):
                poped_element = queue.pop(0)
                temp.append(poped_element.val)
                if poped_element.left is not None:
                    queue.append(poped_element.left)
                if poped_element.right is not None:
                    queue.append(poped_element.right)
            res.append(sum(temp)*1.0/n)
        return res
```