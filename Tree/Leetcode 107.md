# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def levelOrderBottom(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        from collections import deque
        queue = deque()
        queue.append(root)
        res = []
        while queue:
            n = len(queue)
            temp_list = []
            for _ in range(n):
                popped_node = queue.popleft()
                temp_list.append(popped_node.val)
                if popped_node.left:
                    queue.append(popped_node.left)
                if popped_node.right:
                    queue.append(popped_node.right)
            res.append(temp_list)
        return res[::-1]
```