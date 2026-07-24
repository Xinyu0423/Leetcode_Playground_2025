# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: Optional[ListNode]
        :type n: int
        :rtype: Optional[ListNode]
        """
        if head.next is None:
            return None
        temp_head = head
        h = ListNode(-1)
        h.next = head
        p = h.next
        ll_length = 0
        while temp_head is not None:
            temp_head = temp_head.next
            ll_length += 1
        if n == ll_length:
            return h.next.next
        for i in range(ll_length - n - 1):
            p = p.next
        p.next = p.next.next
        p = p.next
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
    def removeNthFromEnd(self, head, n):
        """
        :type head: Optional[ListNode]
        :type n: int
        :rtype: Optional[ListNode]
        """
        h = ListNode(None)
        h.next = head
        fast = h
        slow = h
        for _ in range(n):
            fast = fast.next
        print(fast.val)
        while fast.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        slow = slow.next
        return h.next
```