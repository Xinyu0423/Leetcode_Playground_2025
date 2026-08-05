# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeInBetween(self, list1, a, b, list2):
        """
        :type list1: ListNode
        :type a: int
        :type b: int
        :type list2: ListNode
        :rtype: ListNode
        """
        h = ListNode(-1)
        h.next = list1
        p = h.next
        pre = h
        for i in range(a):
            pre = pre.next
        for j in range(b + 1):
            p = p.next
        pre.next = list2
        temp_p = h.next

        while temp_p.next is not None:
            temp_p = temp_p.next
        temp_p.next = p
        return h.next
```