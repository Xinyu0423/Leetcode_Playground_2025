# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, list1, list2):
        """
        :type list1: Optional[ListNode]
        :type list2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if list1 is None and list2 is None:
            return list1
        elif list1 is None and list2 is not None:
            return list2
        elif list1 is not None and list2 is None:
            return list1
        h = ListNode(None)
        temp_h = h
        p1 = list1
        p2 = list2
        while p1 is not None and p2 is not None:
            if p1.val < p2.val:
                temp_h.next = p1
                temp_h = temp_h.next
                p1 = p1.next
            else:
                temp_h.next = p2
                temp_h = temp_h.next
                p2 = p2.next
        if p1 is None:
            temp_h.next = p2
        elif p2 is None:
            temp_h.next = p1

        return h.next
```