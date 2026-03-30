# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        return self.mergeSort(head)
    
    def mergeSort(self, head):
        if head is None or head.next is None:
            return head
        fast = head.next
        slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        right_head = slow.next
        slow.next = None
        left_bound = self.mergeSort(head)
        right_bound = self.mergeSort(right_head)
        h = ListNode(-1)
        tail = h
        while left_bound and right_bound:
            if left_bound.val < right_bound.val:
                tail.next = left_bound
                left_bound = left_bound.next
            else:
                tail.next = right_bound
                right_bound = right_bound.next
            tail = tail.next
        if left_bound:
            tail.next = left_bound
        if right_bound:
            tail.next = right_bound
        return h.next
```