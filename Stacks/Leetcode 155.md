# Solution 1
```Python
class ListNode:
    def __init__(self, val = None, min_val = None, next = None):
        self.val = val
        self.min_val = min_val
        self.next = next

class MinStack(object):

    def __init__(self):
        self.head = None

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if self.head is None:
            new_node = ListNode()
            new_node.val = val
            new_node.min_val = val
            new_node.next = None
        else:
            new_node = ListNode()
            new_node.val = val
            new_node.min_val = min(val, self.head.min_val)
            new_node.next = self.head
        self.head = new_node
        

    def pop(self):
        """
        :rtype: None
        """
        if self.head is not None:
            self.head = self.head.next
        

    def top(self):
        """
        :rtype: int
        """
        return self.head.val

    def getMin(self):
        """
        :rtype: int
        """
        return self.head.min_val
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

# Solution 2
```Python
class MinStack(object):

    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if len(self.stack) == 0:
            self.stack.append(val)
            self.min_stack.append(val)
        else:
            self.stack.append(val)
            if val <= self.getMin():
                self.min_stack.append(val)
                

    def pop(self):
        """
        :rtype: None
        """
        poped_element = self.stack.pop()
        if poped_element == self.getMin():
            self.min_stack.pop()

        

    def top(self):
        """
        :rtype: int
        """
        return self.stack[-1]
        

    def getMin(self):
        """
        :rtype: int
        """
        return self.min_stack[-1]


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

# Solution 3
```Python
class MinStack(object):

    def __init__(self):
        self.stack = []
        self.min_val = -1
        

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if len(self.stack) == 0:
            self.stack.append(0)
            self.min_val = val
        else:
            self.stack.append(val - self.min_val)
            if val - self.min_val < 0:
                self.min_val = val        

    def pop(self):
        """
        :rtype: None
        """
        poped_val = self.stack.pop()
        if poped_val < 0:
            self.min_val -= poped_val

    def top(self):
        """
        :rtype: int
        """
        if self.stack[-1] < 0:
            return self.min_val
        else:
            return self.min_val + self.stack[-1]
        

    def getMin(self):
        """
        :rtype: int
        """
        return self.min_val


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```