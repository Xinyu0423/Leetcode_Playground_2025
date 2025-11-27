# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isCompleteTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        from collections import deque
        queue = deque()
        queue.append(root)
        flag = False
        while queue:
            popped_node = queue.popleft()
            
            if popped_node is None:
                flag = True
            else:
                if flag:
                    return False
                queue.append(popped_node.left)
                queue.append(popped_node.right)

        return True
```

