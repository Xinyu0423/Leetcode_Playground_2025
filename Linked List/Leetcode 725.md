# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def splitListToParts(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: List[Optional[ListNode]]
        """
        h = ListNode(-1)
        h.next = head
        p = h.next
        length = 0
        while p is not None:
            p = p.next
            length += 1

        p = h.next
        res = []
        if length < k:
            for i in range(k):
                if i < length:
                    temp = p.next
                    p.next = None
                    res.append(p)
                    p = temp
                else:
                    res.append(None)
        else:
            base_size = length // k
            reamainder = length % k
            for i in range(k):
                res.append(p)
                if reamainder > 0:
                    for j in range(base_size):
                        p = p.next
                    reamainder -= 1
                else:
                    for j in range(base_size - 1):
                        p = p.next
                temp = p.next
                p.next = None
                p = temp
        return res
```