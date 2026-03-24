# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        nodes = []
        while head:
            nodes.append(head.val)
            head = head.next
        return nodes == nodes[::-1]
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        h = ListNode(-1)
        h.next = head
        p = h.next
        fast = h.next
        slow = h.next
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        reversed_slow = self.reverse_Linked_list(slow)
        while reversed_slow and head:
            if reversed_slow.val != head.val:
                return False
            reversed_slow = reversed_slow.next
            head = head.next
        return True
    
    def reverse_Linked_list(self, head):
        h = ListNode(-1)
        while head:
            temp_node = head.next
            head.next = h.next
            h.next = head
            head = temp_node
        return h.next
```