# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class CBTInserter(object):

    def __init__(self, root):
        """
        :type root: Optional[TreeNode]
        """
        from collections import deque
        self.root = root
        self.queue = deque()
        self.queue.append(root)
        self.unfilled_node = deque()
        while self.queue:
            popped_node = self.queue.popleft()
            if popped_node.left is None or popped_node.right is None:
                self.unfilled_node.append(popped_node)
            if popped_node.left:
                self.queue.append(popped_node.left)
            if popped_node.right:
                self.queue.append(popped_node.right)
        

    def insert(self, val):
        """
        :type val: int
        :rtype: int
        """
        new_node = TreeNode(val)
        parent_node = self.unfilled_node[0]
        if parent_node.left is None:
            parent_node.left = new_node
        else:
            parent_node.right = new_node
            self.unfilled_node.popleft()
        self.unfilled_node.append(new_node)
        return parent_node.val
        

    def get_root(self):
        """
        :rtype: Optional[TreeNode]
        """
        return self.root
        


# Your CBTInserter object will be instantiated and called as such:
# obj = CBTInserter(root)
# param_1 = obj.insert(val)
# param_2 = obj.get_root()
```