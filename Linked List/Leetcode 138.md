# Soultion 1
```Python
"""
# Definition for a Node.
class Node:
    def __init__(self, x, next=None, random=None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        if head is None:
            return head
        p = head
        while p:
            temp_node = Node(p.val)
            temp_node.next = p.next
            p.next = temp_node
            p = temp_node.next
        
        p = head
        while p:
            if p.random is not None:
                p.next.random = p.random.next
            p = p.next.next
        p = head.next
        res = p
        pre = head
        while p.next is not None:
            pre.next = pre.next.next
            p.next = p.next.next
            pre = pre.next
            p = p.next
            
        pre.next = None
        return res

```