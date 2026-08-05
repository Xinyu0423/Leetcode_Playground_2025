# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        h_1 = ListNode(-1)
        h_1.next = headA
        p_1 = h_1.next

        h_2 = ListNode(-1)
        h_2.next = headB
        p_2 = h_2.next
        
        headA_length = 0
        while headA:
            headA = headA.next
            headA_length += 1
        headA = p_1
        
        headB_length = 0
        while headB:
            headB = headB.next
            headB_length += 1
        headB = p_2
        if headA_length > headB_length:
            for i in range(headA_length - headB_length):
                headA = headA.next
        elif headA_length < headB_length:
            for i in range(headB_length - headA_length):
                headB = headB.next
        for i in range(min(headA_length, headB_length)):
            if headA == headB:
                return headA
            headA = headA.next
            headB = headB.next
        return None
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        temp_headA = headA
        set_A = set()
        while temp_headA:
            set_A.add(temp_headA)
            temp_headA = temp_headA.next
        while headB:
            if headB in set_A:
                return headB
            headB = headB.next
        return None
```

# Solution 3
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        pA = headA
        pB = headB
        while pA != pB:
            if not pA:
                pA = headB
            else:
                pA = pA.next
            if not pB:
                pB = headA
            else:
                pB = pB.next
        return pA
```