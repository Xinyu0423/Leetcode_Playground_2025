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

# Solution 2
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
        self.x_parent = None
        self.y_parent = None
        self.x_depth = 0
        self.y_depth = 0
        self.x = x
        self.y = y
        self.dfs(root, None, 0)
        return self.x_depth == self.y_depth and self.x_parent != self.y_parent

    def dfs(self, root, parent, depth):
        if root is None:
            return None
        if root.val == self.x:
            self.x_parent = parent
            self.x_depth = depth
        if root.val == self.y:
            self.y_parent = parent
            self.y_depth = depth
        self.dfs(root.left, root, depth + 1)
        self.dfs(root.right, root, depth + 1)
```