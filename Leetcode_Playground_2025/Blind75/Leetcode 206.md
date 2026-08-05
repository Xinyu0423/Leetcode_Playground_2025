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

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head is None:
            return head
        from collections import deque
        queue = deque()
        h = ListNode(-1)
        p = head
        while p is not None:
            queue.append(p)
            p = p.next
        while queue:
            popped_node = queue.popleft()
            temp = h.next
            h.next = popped_node
            popped_node.next = temp
        return h.next
```