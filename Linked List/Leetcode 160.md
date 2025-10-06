# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        temp_headA = headA
        temp_headB = headB
        lengthA = 0
        lengthB = 0
        while temp_headA:
            temp_headA = temp_headA.next
            lengthA += 1
        while temp_headB:
            temp_headB = temp_headB.next
            lengthB += 1
        temp_headA = headA
        temp_headB = headB
        if lengthA < lengthB:
            for _ in range(lengthB - lengthA):
                temp_headB = temp_headB.next
        else:
            for _ in range(lengthA - lengthB):
                temp_headA = temp_headA.next
        while temp_headA is not None and temp_headB is not None:
            if temp_headA == temp_headB:
                return temp_headA
            temp_headA = temp_headA.next
            temp_headB = temp_headB.next
        return None
        
```