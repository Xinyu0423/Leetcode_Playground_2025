# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        p1, p2 = l1, l2
        num1, num2 = '', ''
        while p1:
            num1 += str(p1.val)
            p1 = p1.next
        while p2:
            num2 += str(p2.val)
            p2 = p2.next
        num1, num2= int(num1[::-1]), int(num2[::-1])
        res_num = num1 + num2
        res = ListNode(-1)
        p = res
        for num in str(res_num)[::-1]:
            p.next = ListNode(int(num))
            p = p.next
        return res.next            
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        p1, p2 = l1, l2
        carry = 0
        while p1 and p2:
            temp_carry = (p1.val + p2.val + carry) //10
            p1.val = (p1.val +p2.val + carry) % 10
            carry = temp_carry
            if p1.next is None and p2.next is not None:
                p1.next = ListNode(0)
            elif p2.next is None and p1.next is not None:
                p2.next = ListNode(0)
            elif p1.next is None and p2.next is None:
                if carry != 0:
                    p1.next = ListNode(carry)
            p1 = p1.next
            p2 = p2.next
        return l1
```