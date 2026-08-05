# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def nextLargerNodes(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: List[int]
        """
        h = ListNode(-1)
        h.next = head
        p = h.next
        answer = []
        stack = []
        index = 0
        while p is not None:
            while len(stack) > 0 and stack[-1][0].val < p.val:
                poped_element = stack.pop()
                answer[poped_element[1]] = p.val
            answer.append(0)
            stack.append((p, index))
            index += 1
            p = p.next
        return answer              
```