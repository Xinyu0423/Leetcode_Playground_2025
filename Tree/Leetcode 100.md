# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: Optional[TreeNode]
        :type q: Optional[TreeNode]
        :rtype: bool
        """
        if p is None and q is None:
            return True
        elif p is None and q is not None:
            return False
        elif p is not None and q is None:
            return False
        res_p = self.preorder(p)
        res_q = self.preorder(q)
        return res_p == res_q
    
    def preorder(self, root):
        stack = [root]
        res = []
        while len(stack) > 0:
            poped_element = stack.pop()
            if poped_element == -1:
                res.append(None)
            else:
                res.append(poped_element.val)
            if poped_element != -1:
                if poped_element.right is not None:
                    stack.append(poped_element.right)
                else:
                    stack.append(-1)
                if poped_element.left is not None:
                    stack.append(poped_element.left)
                else:
                    stack.append(-1)
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
    def isSameTree(self, p, q):
        """
        :type p: Optional[TreeNode]
        :type q: Optional[TreeNode]
        :rtype: bool
        """
        if p is None and q is None:
            return True
        elif p is None and q is not None:
            return False
        elif p is not None and q is None:
            return False
        elif p.val != q.val:
            return False
        else:
            return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```