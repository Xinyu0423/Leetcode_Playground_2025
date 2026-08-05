# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def deepestLeavesSum(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        from collections import deque
        queue = deque()
        queue.append(root)
        res = []
        while queue:
            n = len(queue)
            level_list = []
            for _ in range(n):
                popped_element = queue.popleft()
                level_list.append(popped_element.val)
                if popped_element.left:
                    queue.append(popped_element.left)
                if popped_element.right:
                    queue.append(popped_element.right)

            res = level_list
        return sum(res)
```

# Solution 2
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def deepestLeavesSum(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        self.max_depth = 0
        self.res = 0
        self.dfs(root, 0)
        return self.res

    def dfs(self, root, depth):
        if root is None:
            return None
        if root.left is None and root.right is None:
            if depth > self.max_depth:
                self.max_depth = depth
                self.res = root.val
            elif depth == self.max_depth:
                self.res += root.val
        self.dfs(root.left, depth + 1)
        self.dfs(root.right, depth + 1)
```