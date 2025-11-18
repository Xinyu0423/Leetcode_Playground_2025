# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def reverseOddLevels(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: Optional[TreeNode]
        """
        level = 0
        queue = [root]
        while queue:
            level += 1
            level_node = []
            for _ in range(len(queue)):
                popped_element = queue.pop(0)
                level_node.append(popped_element)
                if popped_element.left:
                    queue.append(popped_element.left)
                if popped_element.right:
                    queue.append(popped_element.right)
            if level % 2 == 0:
                i = 0
                j = len(level_node) - 1
                while i < j:
                    temp = level_node[i].val
                    level_node[i].val = level_node[j].val
                    level_node[j].val = temp
                    i += 1
                    j -= 1
        return root
```