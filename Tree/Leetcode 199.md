# Solution 1
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
        if root is None:
            return []
        self.res = []
        self.preorder(root, 0)
        return self.res

    def preorder(self, root, height):
        if root is None:
            return None
        if len(self.res) == height:
            self.res.append(root.val)
        else:
            self.res[height] = root.val
        self.preorder(root.left, height + 1)
        self.preorder(root.right, height + 1)
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
    def rightSideView(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        queue = [root]
        res = []
        while queue:
            n = len(queue)
            temp_res = None
            for _ in range(n):
                popped_element = queue.pop(0)
                temp_res = popped_element.val
                if popped_element.left is not None:
                    queue.append(popped_element.left)
                if popped_element.right is not None:
                    queue.append(popped_element.right)
            res.append(temp_res)
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
    def rightSideView(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if root is None:
            return []
        queue = [root]
        last = root
        q = None
        res = []
        while queue:
            popped_element = queue.pop(0)
            if popped_element.left:
                q = popped_element.left
                queue.append(popped_element.left)
            if popped_element.right:
                q = popped_element.right
                queue.append(popped_element.right)
            if popped_element == last:
                res.append(last.val)
                last = q
        return res
```