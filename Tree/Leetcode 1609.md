# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isEvenOddTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        from collections import deque
        queue = deque()
        queue.append(root)
        level = 0
        last = root
        level_list = []
        temp_node = None
        while queue:
            popped_node = queue.popleft()
            level_list.append(popped_node.val)
            if popped_node.left:
                temp_node = popped_node.left
                queue.append(temp_node)
            if popped_node.right:
                temp_node = popped_node.right
                queue.append(temp_node)
            
            if popped_node == last:
                print(level_list)
                if level % 2 == 0:
                    if len(level_list) == 1 and level_list[0] % 2 == 0:
                        return False
                    for i in range(1, len(level_list)):
                        if level_list[i] <= level_list[i - 1] or level_list[i] % 2 == 0:
                            return False
                if level % 2 == 1:
                    if len(level_list) == 1 and level_list[0] % 2 == 1:
                        return False
                    for i in range(1, len(level_list)):
                        if level_list[i] >= level_list[i - 1] or level_list[i] % 2 == 1:
                            return False
                level += 1
                level_list = []
                last = temp_node
        return True 
```