# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def minDepth(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if root is None:
            return 0
        from collections import deque
        level = 0
        queue = deque()
        queue.append(root)
        while queue:
            n = len(queue)
            level += 1
            for _ in range(n):
                popped_node = queue.popleft()
                if popped_node.left:
                    queue.append(popped_node.left)
                if popped_node.right:
                    queue.append(popped_node.right)
                if popped_node.left is None and popped_node.right is None:
                    return level
        return level
        
```