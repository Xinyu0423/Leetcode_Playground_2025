# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        h = ListNode(-1)
        p = head
        while p is not None:
            temp = p.next
            p.next = h.next
            h.next = p
            p = temp
        return h.next
```