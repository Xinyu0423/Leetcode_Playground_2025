# Solution 1 (Ji)
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # Create two dummy nodes: one for even-indexed list, one for odd-indexed list
        even = ListNode(-10000000)
        odd = ListNode(-10000000)
        even_res = even
        odd_res = odd
        ind = 0
        while head:
            # Node goes to the even list
            if ind % 2 == 0:
                even.next = head
                even = even.next
            else:
                # Node goes to the odd list
                odd.next = head
                odd = odd.next
            head = head.next
            ind += 1
        # End the odd list properly to avoid cycles
        odd.next = None
        # Connect even list to odd list
        even.next = odd_res.next
        return even_res.next
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def oddEvenList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        odd_LL = ListNode(-1)
        even_LL = ListNode(-1)
        res = odd_LL
        temp_even= even_LL
        p = head
        while p is not None:
            odd_LL.next = p
            odd_LL = p
            p = p.next
            if p is not None:
                even_LL.next = p
                even_LL = p
                p = p.next
        
        odd_LL.next = temp_even.next
        even_LL.next = None
        return res.next
        
```