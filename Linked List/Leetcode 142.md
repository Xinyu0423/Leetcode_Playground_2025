# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        fast = head
        slow = head
        h = ListNode(None)
        h.next = head
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                break
            
        if slow is None:
            return None
        slow = h.next
        while fast is not None and  fast.next is not None:
            if fast == slow:
                return slow
            fast = fast.next
            slow = slow.next
```