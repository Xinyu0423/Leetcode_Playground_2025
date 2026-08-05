# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        h = ListNode(None)
        h.next = head
        pre = h
        p = h.next
        while p is not None:
            if pre.val == p.val :
                pre.next = p.next
                p = pre.next
                
            else:
                p = p.next
                pre = pre.next
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
    def deleteDuplicates(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if head is None or head.next is None:
            return head
        pre = head
        p = head.next
        while p is not None:
            if pre.val != p.val:
                pre.next = p
                pre = p
            p = p.next
        pre.next = None
        return head
```