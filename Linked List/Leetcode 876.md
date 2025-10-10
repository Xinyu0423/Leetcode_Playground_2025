# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def middleNode(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        h.next = head
        fast = h.next
        slow = h.next
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
        return slow
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def middleNode(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        h.next = head
        p = h.next
        length = 0
        while p is not None:
            p = p.next
            length += 1
        p = h.next
        for _ in range(length//2):
            p = p.next
        return p
```