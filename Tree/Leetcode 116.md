# Solution 1
```Python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val=0, left=None, right=None, next=None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution(object):
    def connect(self, root):
        """
        :type root: Node
        :rtype: Node
        """
        if root is None:
            return None
        from collections import deque
        queue = deque()
        queue.append(root)
        while queue:
            n = len(queue)
            temp_list = []
            for _ in range(n):
                popped_element = queue.popleft()
                temp_list.append(popped_element)
                if popped_element.left:
                    queue.append(popped_element.left)
                if popped_element.right:
                    queue.append(popped_element.right)
            for i in range(len(temp_list)):
                if i != len(temp_list) - 1:
                    temp_list[i].next = temp_list[i + 1]
                else:
                    temp_list[i].next = None
        return root
```

# Solution 2
```Python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val=0, left=None, right=None, next=None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution(object):
    def connect(self, root):
        """
        :type root: Node
        :rtype: Node
        """
        if root is None:
            return None
        leftmost = root
        while leftmost.left is not None:
            head = leftmost
            while head is not None:
                head.left.next = head.right
                if head.next is not None:
                    head.right.next = head.next.left
                head = head.next
            leftmost = leftmost.left
        return root
```