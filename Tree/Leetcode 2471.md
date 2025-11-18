# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def minimumOperations(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if root is None:
            return 0
        queue = [root]
        self.res = 0
        while len(queue) > 0:
            level_list = []
            n = len(queue)
            for i in range(n):
                poped_element = queue.pop(0)
                level_list.append(poped_element.val)
                if poped_element.left is not None:
                    queue.append(poped_element.left)
                if poped_element.right is not None:
                    queue.append(poped_element.right)
            self.minSwap(level_list)
        return self.res
        

    
    def minSwap(self, level_list):
        temp_list = sorted(level_list)
        h_map = {}
        for i in range(len(temp_list)):
            h_map[temp_list[i]] = i
        for i in range(len(level_list)):
            while level_list[i] != temp_list[i]:
                temp = level_list[h_map[level_list[i]]]
                level_list[h_map[level_list[i]]] = level_list[i]
                level_list[i] = temp
                self.res += 1
        return None
```