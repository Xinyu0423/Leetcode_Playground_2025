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
        temp = h.next
            
        
        while p is not None and p.next is not None:
            if p.val == p.next.val:
                duplicate_val = p.val
                while p is not None and p.val == duplicate_val:
                    p = p.next
                pre.next = p
            else:
                pre = pre.next
                p = p.next

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
        counter = [0 for _ in range(201)]
        p = head
        while p is not None:
            counter[p.val + 100] += 1
            p = p.next
        h = ListNode(None)
        temp_h = h
        p = head
        while p is not None:
            if counter[p.val + 100] == 1:
                temp_h.next = p
                temp_h = p
            p = p.next
        temp_h.next = None
        return h.next

        
```