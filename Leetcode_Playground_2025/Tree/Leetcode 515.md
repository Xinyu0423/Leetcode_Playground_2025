# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def largestValues(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        from collections import deque
        queue = deque()
        queue.append(root)
        last = root
        res = []
        temp_node = None
        level_max = float("-inf")
        while queue:
            popped_element = queue.popleft()
            level_max = max(popped_element.val, level_max)
            if popped_element.left is not None:
                temp_node = popped_element.left
                queue.append(temp_node)
            if popped_element.right is not None:
                temp_node = popped_element.right
                queue.append(temp_node)
            if popped_element == last:
                last = temp_node
                res.append(level_max)
                level_max = float("-inf")
        return res
```