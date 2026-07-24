# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        if head is None or head.next is None:
            return head
        from collections import deque
        h = ListNode(-1)
        h.next = head
        p = h.next
        queue = deque()
        while p is not None:
            queue.append(p)
            p = p.next
        p = h.next
        length = 1
        while queue:
            if length % 2 == 0:
                popped_element = queue.pop()
            else:
                popped_element = queue.popleft()
            popped_element.next = None
            p.next = popped_element
            p = p.next
            length += 1
        return h.next
```