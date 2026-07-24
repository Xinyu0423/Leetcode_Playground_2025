# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        p = head
        while p:
            temp_node = p.next
            p.next = h.next
            h.next = p
            p = temp_node
        return h.next
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        pre = None
        p = head
        while p:
            temp = p.next
            p.next = pre
            pre = p
            p = temp
        return pre
```

# Solution 3 (Ji)
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_node = ListNode(-1)
        result = dummy_node
        l = []
        while head:
            l.append(head.val)
            head = head.next
        for i in range(len(l)-1, -1, -1):
            dummy_node.next = ListNode(l[i])
            dummy_node =  dummy_node.next
        dummy_node.next = None
        return result.next
```