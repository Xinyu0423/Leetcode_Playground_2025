# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        from collections import deque
        levels = 0
        queue = deque()
        queue.append(root)
        while queue:
            n = len(queue)
            levels += 1
            for i in range(n):
                popped_node = queue.popleft()
                if popped_node.left:
                    queue.append(popped_node.left)
                if popped_node.right:
                    queue.append(popped_node.right)
        return levels
```