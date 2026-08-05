# Solution 1
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        while head != None and head.val == val:
            head = head.next
        if head is None:
            return None
        temp_head = head
        pre = head
        temp_head = temp_head.next

        while temp_head != None:
            if temp_head.val == val:
                pre.next = temp_head.next
                temp_head = temp_head.next
            else:
                pre = temp_head
                temp_head = temp_head.next
        return head
```

# Solution 1 (Ji - space O(1), time O(n))
```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        # Step 1: move head forward if the first nodes contain the target value
        while head and head.val == val:
            head = head.next   # skip nodes equal to val

        # If the list becomes empty after removing from the front
        if not head:
            return None

        # Step 2: use two pointers for the rest of the list
        pre = head          # last node we keep
        curr = head.next    # node under inspection

        # Step 3: traverse and remove nodes in-place
        while curr:
            if curr.val == val:
                # skip the current node by linking pre to curr.next
                pre.next = curr.next
            else:
                # keep the node, so move pre forward
                pre = pre.next
            # always move curr forward
            curr = curr.next

        # Step 4: return the updated head
        return head
```

# Solution 2
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        h = ListNode(-1)
        p = head
        temp_h = h
        while p is not None:
            if p.val != val:
                temp_h.next = p
                temp_h = p
            p = p.next
        temp_h.next = None
        return h.next
```
# Solution 2 (Ji - space O(1), time O(n))
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        if not head:
            return
        # Create a dummy node before the actual head. It will be used to created a new linked list
        # This helps handle cases where the head itself needs to be removed
        temp_head = ListNode(-1)
        # keep a reference to the dummy node(for returning later), always point to the first linked list 
        res = temp_head # shallow copy
        # Traverse the original list
        while head:
            if head.val != val:
                temp_head.next = head
                temp_head = temp_head.next
            head = head.next
        # Important: break the link at the end of the new list
        # Otherwise the last node may still point to unwanted old nodes
        temp_head.next = None
        return res.next
```
# Solution 3
```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        if head==None:
            return head
        head.next=self.removeElements(head.next,val)
        if head.val==val:
            return head.next
        else:
            return head
```