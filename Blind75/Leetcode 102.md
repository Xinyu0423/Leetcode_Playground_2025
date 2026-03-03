# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:
            return []
        from collections import deque
        queue = deque()
        queue.append(root)
        res = []
        while queue:
            level_list = []
            n = len(queue)
            for i in range(n):
                poped_node = queue.popleft()
                level_list.append(poped_node.val)
                if poped_node.left:
                    queue.append(poped_node.left)
                if poped_node.right:
                    queue.append(poped_node.right)
            res.append(level_list)
        return res
```