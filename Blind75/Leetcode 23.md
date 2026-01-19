# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if len(lists) == 0:
            return None
        elif (lists) == 1:
            return lists[0]
        h = lists[0]
        for i in range(1, len(lists)):
            h = self.merge_two_linked_list(h, lists[i])
        return h
    
    def merge_two_linked_list(self, list1, list2):
        if list1 is None and list2 is None:
            return None
        elif list1 is None and list2:
            return list2
        elif list1 and list2 is None:
            return list1
        h = ListNode(-1)
        p = h
        while list1 and list2:
            if list1.val < list2.val:
                p.next = list1
                list1 = list1.next
            else:
                p.next = list2
                list2 = list2.next
            p = p.next
        if list1 is None:
            p.next = list2
        else:
            p.next = list1
        return h.next
```