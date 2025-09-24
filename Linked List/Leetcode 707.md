# Solution 1
```Python
class ListNode:
    def  __init__(self, val = -1):
        self.val = val
        self.next = None
    
class MyLinkedList(object):

    def __init__(self):
        self.length = 0
        self.head = ListNode()
        

    def get(self, index):
        """
        :type index: int
        :rtype: int
        """
        if index < 0 or index >= self.length:
            return -1
        p = self.head
        for _ in range(index + 1):
            p = p.next
        return p.val
        

    def addAtHead(self, val):
        """
        :type val: int
        :rtype: None
        """
        return self.addAtIndex(0, val)
        

    def addAtTail(self, val):
        """
        :type val: int
        :rtype: None
        """
        return self.addAtIndex(self.length, val)
        

    def addAtIndex(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        if index < 0 or index > self.length:
            return None
        
        p = self.head
        added_node = ListNode(val)
        for i in range(index):
            p = p.next
        added_node.next = p.next
        p.next = added_node
        self.length += 1
        return self.head
        

    def deleteAtIndex(self, index):
        """
        :type index: int
        :rtype: None
        """
        if index < 0 or index >= self.length:
            return None
        p = self.head
        for i in range(index):
            p = p.next
        s = p.next
        p.next = s.next
        self.length -= 1
        


# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```

# Soulion 2
```Python
class Node:
    def __init__(self, val = -1, next = None):
        self.val = val
        self.next = next

class MyLinkedList(object):
    def __init__(self):
        self.rear = None
        self.length = 0

    def get(self, index):
        """
        :type index: int
        :rtype: int
        """
        if index < 0 or index >= self.length:  # 修正索引检查
            return -1
        if self.length == 0:
            return -1
            
        # 从头节点开始遍历
        p = self.rear.next if self.rear else None
        for i in range(index):
            p = p.next
        return p.val

    def addAtHead(self, val):
        """
        :type val: int
        :rtype: None
        """
        new_node = Node(val)
        if self.length == 0:
            new_node.next = new_node
            self.rear = new_node
        else:
            new_node.next = self.rear.next
            self.rear.next = new_node
        self.length += 1

    def addAtTail(self, val):
        """
        :type val: int
        :rtype: None
        """
        new_node = Node(val)
        if self.length == 0:
            new_node.next = new_node
            self.rear = new_node
        else:
            new_node.next = self.rear.next
            self.rear.next = new_node
            self.rear = new_node
        self.length += 1

    def addAtIndex(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        if index < 0 or index > self.length:
            return
        
        if index == 0:
            self.addAtHead(val)
            return
        elif index == self.length:
            self.addAtTail(val)
            return
            
        # 找到要插入位置的前一个节点
        p = self.rear.next
        for i in range(index - 1):
            p = p.next
            
        new_node = Node(val)
        new_node.next = p.next
        p.next = new_node
        self.length += 1

    def deleteAtIndex(self, index):
        """
        :type index: int
        :rtype: None
        """
        if index < 0 or index >= self.length:  # 修正索引检查
            return
            
        if self.length == 1:
            self.rear = None
        else:
            if index == 0:
                # 删除头节点
                self.rear.next = self.rear.next.next
            else:
                # 找到要删除节点的前一个节点
                pre = self.rear.next
                for i in range(index - 1):
                    pre = pre.next
                # 删除节点
                pre.next = pre.next.next
                # 如果删除的是尾节点，更新rear
                if index == self.length - 1:
                    self.rear = pre
        self.length -= 1
```