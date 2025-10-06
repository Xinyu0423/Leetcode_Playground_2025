# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def insertionSortList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        p = head
        while p is not None:
            temp = p.next
            pre = h
            next_node = h.next
            while next_node is not None and next_node.val < p.val:
                pre = pre.next
                next_node = next_node.next
            p.next = next_node
            pre.next = p
            p = temp
        return h.next
```