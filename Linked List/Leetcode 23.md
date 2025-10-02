# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[Optional[ListNode]]
        :rtype: Optional[ListNode]
        """
        if len(lists) == 0:
            return None
        if len(lists) == 1:
            return lists[0]
        h = lists[0]
        for i in range(1, len(lists)):
            h = self.merge(h, lists[i])
        return h
    
    def merge(self, list1, list2):
        if list1 is None and list2 is None:
            return None
        elif list1 is None and list2 is not None:
            return list2
        elif list1 is not None and list2 is None:
            return list1
        h = ListNode(-1)
        temp_h = h
        while list1 is not None and list2 is not None:
            if list1.val < list2.val:
                temp_h.next = list1
                temp_h = list1
                list1 = list1.next
            else:
                temp_h.next = list2
                temp_h = list2
                list2 = list2.next    
        if list1 is None and list2 is not None:
            temp_h.next = list2
        if list1 is not None and list2 is None:
            temp_h.next = list1
        return h.next   
```

Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[Optional[ListNode]]
        :rtype: Optional[ListNode]
        """
        if len(lists) == 0:
            return None
        h = ListNode(-1)
        temp_h = h
        x = [0 for _ in range(len(lists))]
        for i in range(len(lists)):
            if lists[i] is None:
                x[i] = float('inf')
            else:
                x[i] = lists[i].val
        while True:
            mini = self.mink(x, len(lists))
            if mini == -1:
                break
            temp_h.next = lists[mini]
            temp_h = lists[mini]
            lists[mini] = lists[mini].next
            if lists[mini] != None:
                x[mini] = lists[mini].val
            else:
                x[mini] = float('inf')
        return h.next

    def mink(self, x, k):
        mini = 0
        for i in range(1, k):
            if x[i] < x[mini]:
                mini = i
        if x[mini] == float('inf'):
            return -1
        else:
            return mini
```