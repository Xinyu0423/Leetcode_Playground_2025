# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def partition(self, head, x):
        """
        :type head: Optional[ListNode]
        :type x: int
        :rtype: Optional[ListNode]
        """
        h1 = ListNode(None)
        h2 = ListNode(None)
        res = h1
        temp_h2 = h2
        while head is not None:
            if head.val < x:
                h1.next = head
                h1 = h1.next
            else:
                temp_h2.next = head
                temp_h2 = temp_h2.next
            head = head.next
        temp_h2.next = None
        h1.next = h2.next
        return res.next
                
```