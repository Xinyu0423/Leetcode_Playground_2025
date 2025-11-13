# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        queue = [[root, 1]]
        level = 1
        temp_res = []
        res = []
        while queue:
            poped_root, temp_level = queue.pop(0)
            if poped_root.left is not None:
                queue.append([poped_root.left, temp_level + 1])
            if poped_root.right is not None:
                queue.append([poped_root.right, temp_level + 1])
            if temp_level == level:
                temp_res.append(poped_root.val)
            else:
                res.append(temp_res)
                temp_res = [poped_root.val]
                level += 1
        res.append(temp_res)
        return res
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
    def levelOrder(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        queue = [root]
        last = root
        res = []
        temp_res = []
        q = None
        while queue:
            popped_element = queue.pop(0)
            if popped_element.left:
                q = popped_element.left
                queue.append(popped_element.left)
            if popped_element.right:
                q = popped_element.right
                queue.append(popped_element.right)
            temp_res.append(popped_element.val)
            if popped_element == last:
                res.append(temp_res)
                last = q
                temp_res = []
        return res
```

# Solution 3
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        queue = [root]
        res = []
        while queue:
            temp_res = []
            n = len(queue)
            for _ in range(n):
                poped_element = queue.pop(0)
                temp_res.append(poped_element.val)
                if poped_element.left is not None:
                    queue.append(poped_element.left)
                if poped_element.right is not None:
                    queue.append(poped_element.right)
            res.append(temp_res)
        return res
```

# Solution 4
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def rightSideView(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root == None:
            return []
        queue = [[root, 1]]
        level = 1
        res = []
        temp_res = None
        while queue:
            popped_root, temp_level = queue.pop(0)
            if popped_root.left:
                queue.append([popped_root.left, temp_level + 1])
            if popped_root.right:
                queue.append([popped_root.right, temp_level + 1])
            if temp_level == level:
                temp_res = popped_root.val
            else:
                level = temp_level
                res.append(temp_res)
                temp_res = popped_root.val
        if temp_res is not None:
            res.append(temp_res)
        return res
```