# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseBetween(self, head, left, right):
        """
        :type head: Optional[ListNode]
        :type left: int
        :type right: int
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        h.next = head
        p = h.next
        pre = h
        for _ in range(left - 1):
            pre= pre.next
            p = p.next

        for _ in range(right - left):
            temp = p.next
            p.next = p.next.next
            temp.next = pre.next
            pre.next = temp
        return h.next

```