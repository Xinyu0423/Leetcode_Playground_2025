# Solution 1
```Python
class DinnerPlates(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.stack = []
        self.avilable = set()
        

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if len(self.avilable) > 0:
            min_index = min(self.avilable)
            self.stack[min_index].append(val)
            if len(self.stack[min_index]) == self.capacity:
                self.avilable.remove(min_index)
        else:
            self.stack.append([val])
            self.avilable.add(len(self.stack) - 1)
            if len(self.stack[len(self.stack) - 1]) == self.capacity:
                self.avilable.remove(len(self.stack) - 1)


    def pop(self):
        """
        :rtype: int
        """
        if len(self.stack) == 0:
            return -1
        while len(self.stack) > 0 and len(self.stack[-1]) == 0:
            removed_index = len(self.stack) - 1
            self.stack.pop()
            self.avilable.remove(removed_index)
        
        if len(self.stack) == 0:
            return -1
        poped_element = self.stack[len(self.stack) - 1].pop()
        if len(self.stack[len(self.stack) - 1]) == 0:
            removed_index = len(self.stack) -1
            self.stack.pop()
            if removed_index in self.avilable:
                self.avilable.remove(removed_index)
        else:
            self.avilable.add(len(self.stack) - 1)
        return poped_element


    def popAtStack(self, index):
        """
        :type index: int
        :rtype: int
        """
        if index >= len(self.stack) or len(self.stack[index]) == 0:
            return -1
        poped_element = self.stack[index].pop()
        self.avilable.add(index)
        return poped_element


# Your DinnerPlates object will be instantiated and called as such:
# obj = DinnerPlates(capacity)
# obj.push(val)
# param_2 = obj.pop()
# param_3 = obj.popAtStack(index)
```