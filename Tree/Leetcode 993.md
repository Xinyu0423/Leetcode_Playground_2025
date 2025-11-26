# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isCousins(self, root, x, y):
        """
        :type root: Optional[TreeNode]
        :type x: int
        :type y: int
        :rtype: bool
        """
        from collections import deque
        queue = deque()
        queue.append([root, None])
        while queue:
            n = len(queue)
            level_list = []
            parent_map = {}
            for _ in range(n):
                popped_node, parent_node = queue.popleft()
                parent_map[popped_node.val] = parent_node
                level_list.append(popped_node.val)
                if popped_node.left:
                    queue.append([popped_node.left, popped_node])
                if popped_node.right:
                    queue.append([popped_node.right, popped_node])
            if x in level_list and y in level_list:
                if parent_map[x] != parent_map[y]:
                    return True
        return False
```