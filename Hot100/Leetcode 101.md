# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if root is None:
            return True
        if root.left and root.right is None:
            return False
        if root.left is None and root.right:
            return False
        if root.left is None and root.right is None:
            return True
        return self.dfs(root.left, root.right)
        
    def dfs(self, left_node, right_node):
        
        # 如果左树的左孩子与右树的右孩子对称，左树的右孩子与右树的左孩子对称，那么这个左树和右树就对称。
        if left_node is None and right_node is None:
            return True
        if left_node and right_node is None:
            return False
        if left_node is None and right_node:
            return False
        if left_node.val != right_node.val:
            return False
        return self.dfs(left_node.right, right_node.left) and self.dfs(left_node.left, right_node.right)
```

# Solution 2
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        from collections import deque
        if root is None:
            return True
        queue = deque()
        queue.append(root)
        while queue:
            level_list = []
            n = len(queue)
            for _ in range(n):
                popped_node = queue.popleft()
                if popped_node is not None:
                    level_list.append(popped_node.val)
                else:
                    level_list.append(None)
                if popped_node is not None:
                    if popped_node.left:
                        queue.append(popped_node.left)
                    else:
                        queue.append(None)
                    if popped_node.right:
                        queue.append(popped_node.right)
                    else:
                        queue.append(None)
            if level_list != level_list[::-1]:
                return False
        return True
```