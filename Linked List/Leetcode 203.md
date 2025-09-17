# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        while head != None and head.val == val:
            head = head.next
        if head is None:
            return None
        temp_head = head
        pre = head
        temp_head = temp_head.next

        while temp_head != None:
            if temp_head.val == val:
                pre.next = temp_head.next
                temp_head = temp_head.next
            else:
                pre = temp_head
                temp_head = temp_head.next
        return head
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        p = head
        temp_h = h
        while p is not None:
            if p.val != val:
                temp_h.next = p
                temp_h = p
            p = p.next
        temp_h.next = None
        return h.next
```

# Solution 3
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        if head==None:
            return head
        head.next=self.removeElements(head.next,val)
        if head.val==val:
            return head.next
        else:
            return head
```