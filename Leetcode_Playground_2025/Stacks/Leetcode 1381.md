# Solution 1
```Python
class CustomStack(object):

    def __init__(self, maxSize):
        """
        :type maxSize: int
        """
        self.stack = []
        self.size = 0
        self.maxSize = maxSize
        

    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        if self.size < self.maxSize:
            self.stack.append(x)
            self.size += 1
        
        

    def pop(self):
        """
        :rtype: int
        """
        if self.size > 0:
            poped_element = self.stack.pop()
            self.size -= 1
            return poped_element
        else:
            return -1 

    def increment(self, k, val):
        """
        :type k: int
        :type val: int
        :rtype: None
        """
        if self.size < k:
            for i in range(len(self.stack)):
                self.stack[i] = self.stack[i] + val
        else:
            for i in range(k):
                self.stack[i] = self.stack[i] + val


# Your CustomStack object will be instantiated and called as such:
# obj = CustomStack(maxSize)
# obj.push(x)
# param_2 = obj.pop()
# obj.increment(k,val)
```