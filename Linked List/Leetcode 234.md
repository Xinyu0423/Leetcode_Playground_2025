# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: bool
        """
        h = ListNode(-1)
        h.next = head
        p = h.next
        fast = h.next
        slow = h.next
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
        reversed_slow = ListNode(-1)
        while slow is not None:
            temp = slow.next
            slow.next = reversed_slow.next
            reversed_slow.next = slow
            slow = temp
        reversed_slow = reversed_slow.next

        while reversed_slow is not None:
            if p.val != reversed_slow.val:
                return False
            p = p.next
            reversed_slow = reversed_slow.next
        return True
```