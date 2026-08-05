# Solution 1(双向链表)
```Python
class ListNode:
    def __init__(self, val = '', next = None, prev = None):
        self.val = val
        self.next = next
        self.prev = prev

class TextEditor(object):

    def __init__(self):
        self.head = ListNode()
        self.tail = ListNode()
        self.head.next = self.tail
        self.tail.prev = self.head
        self.cursor = self.head

    def addText(self, text):
        """
        :type text: str
        :rtype: None
        """
        for char in text:
            temp_node = ListNode(char, self.cursor.next, self.cursor)
            self.cursor.next.prev = temp_node
            self.cursor.next = temp_node
            self.cursor = temp_node

    def deleteText(self, k):
        """
        :type k: int
        :rtype: int
        """
        deleted = 0
        while deleted < k and self.cursor != self.head:
            prev_node = self.cursor.prev
            prev_node.next = self.cursor.next
            self.cursor.next.prev = prev_node
            self.cursor = prev_node
            deleted += 1
        return deleted
        

    def cursorLeft(self, k):
        """
        :type k: int
        :rtype: str
        """
        for _ in range(k):
            if self.cursor == self.head:
                break
            self.cursor = self.cursor.prev
        res = ''
        node = self.cursor
        count = 0
        while node != self.head and count < 10:
            res += node.val
            node = node.prev
            count += 1
        
        return res[::-1]
        

    def cursorRight(self, k):
        """
        :type k: int
        :rtype: str
        """
        for _ in range(k):
            if self.cursor.next == self.tail:
                break
            self.cursor = self.cursor.next
        
        res = ''
        node = self.cursor
        count = 0
        while node != self.head and count < 10:
            res += node.val
            node = node.prev
            count += 1
        
        return res[::-1]
        


# Your TextEditor object will be instantiated and called as such:
# obj = TextEditor()
# obj.addText(text)
# param_2 = obj.deleteText(k)
# param_3 = obj.cursorLeft(k)
# param_4 = obj.cursorRight(k)
```

# Solution 2(单链表，会超时)
```Python
class ListNode:
    def __init__(self, val = '', next = None):
        self.val = val
        self.next = next

class TextEditor(object):

    def __init__(self):
        self.left_head = ListNode('')
        self.left_tail = self.left_head
        self.right_head = None
        self.left_size = 0

    def addText(self, text):
        """
        :type text: str
        :rtype: None
        """
        for char in text:
            new_node = ListNode(char)
            self.left_tail.next = new_node
            self.left_tail = new_node
            self.left_size += 1

    def deleteText(self, k):
        """
        :type k: int
        :rtype: int
        """
        if k > self.left_size:
            k = self.left_size
        p = self.left_head
        for i in range(self.left_size - k):
            p = p.next
        p.next = None
        self.left_tail = p
        self.left_size -= k
        return k        

    def cursorLeft(self, k):
        """
        :type k: int
        :rtype: str
        """
        if k > self.left_size:
            k = self.left_size
        if k == 0:
            return self.get_text()
        prev = self.left_head
        for _ in range(self.left_size - k):
            prev = prev.next
        node_to_move = prev.next
        prev.next = None

        if node_to_move is not None:
            tail = node_to_move
            while tail.next is not None:
                tail = tail.next
            tail.next = self.right_head
            self.right_head = node_to_move

        self.left_tail = prev
        self.left_size -= k
        return self.get_text()

        

    def cursorRight(self, k):
        """
        :type k: int
        :rtype: str
        """
        count = 0
        p = self.right_head
        while p is not None and count < k:
            p = p.next
            count += 1
        
        for _ in range(count):
            if self.right_head is not None:
                node_to_move = self.right_head
                self.right_head = self.right_head.next
                node_to_move.next = None
                self.left_tail.next = node_to_move
                self.left_tail = node_to_move
                self.left_size += 1
        return self.get_text()
        
    
    def get_text(self):
        res = []
        start_pos = max(0, self.left_size - 10)
        p = self.left_head.next
        for _ in range(start_pos):
            p = p.next
        count = 0
        while p is not None and count < 10:
            res.append(p.val)
            p = p.next
            count += 1
        return ''.join(res)


# Your TextEditor object will be instantiated and called as such:
# obj = TextEditor()
# obj.addText(text)
# param_2 = obj.deleteText(k)
# param_3 = obj.cursorLeft(k)
# param_4 = obj.cursorRight(k)
```