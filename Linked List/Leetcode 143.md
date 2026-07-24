# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reorderList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: None Do not return anything, modify head in-place instead.
        """
        if head is None or head.next is None:
            return head
        h = ListNode(-1)
        h.next = head
        p = h.next
        fast = p
        slow = p
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next


        reversed_h = ListNode(-1)
        while slow is not None:
            temp = slow.next
            slow.next = reversed_h.next
            reversed_h.next = slow
            slow = temp

        while p.next.next is not None:
            p = p.next
        p.next = None
        p = h.next

        reversed_h = reversed_h.next
        while p.next is not None:
            temp_p = p.next
            temp_reversed_h = reversed_h.next
            p.next = reversed_h
            reversed_h.next = temp_p
            p = temp_p
            reversed_h = temp_reversed_h
        if reversed_h is not None:
            p.next = reversed_h   

        return h.next
        
```