# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def diameterOfBinaryTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if root == None:
            return None
        stack = [[root, False]]
        max_diameter = 0
        depth = {}
        while len(stack) > 0:
            temp_root, visited = stack.pop()
            if visited:
                if temp_root.left:
                    left_depth = depth.get(temp_root.left, 0)
                else:
                    left_depth = 0
                if temp_root.right:
                    right_depth = depth.get(temp_root.right, 0)
                else:
                    right_depth = 0
                depth[temp_root] = max(left_depth, right_depth) + 1
                max_diameter = max(max_diameter, left_depth + right_depth)
            else:
                stack.append([temp_root, True])
                if temp_root.left:
                    stack.append([temp_root.left, False])
                if temp_root.right:
                    stack.append([temp_root.right, False])
        return max_diameter
```

```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def diameterOfBinaryTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        self.res = 0
        self.depth(root)
        return self.res
    
    def depth(self, root):
        if root == None:
            return 0
        left_depth = self.depth(root.left)
        right_depth = self.depth(root.right)
        self.res = max(self.res, left_depth + right_depth)
        return max(left_depth, right_depth) + 1
```