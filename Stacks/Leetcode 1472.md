# Solution 1
```Python
class BrowserHistory(object):

    def __init__(self, homepage):
        """
        :type homepage: str
        """
        self.visit_stack = [homepage]
        self.forward_stack = []

        

    def visit(self, url):
        """
        :type url: str
        :rtype: None
        """
        self.visit_stack.append(url)
        self.forward_stack = []
        

    def back(self, steps):
        """
        :type steps: int
        :rtype: str
        """
        steps = min(steps, len(self.visit_stack) - 1)
        for _ in range(steps):
            poped_element = self.visit_stack.pop()
            self.forward_stack.append(poped_element)
        return self.visit_stack[-1]
        

    def forward(self, steps):
        """
        :type steps: int
        :rtype: str
        """
        steps = min(steps, len(self.forward_stack))
        for _ in range(steps):
            poped_element = self.forward_stack.pop()
            self.visit_stack.append(poped_element)
        return self.visit_stack[-1]


# Your BrowserHistory object will be instantiated and called as such:
# obj = BrowserHistory(homepage)
# obj.visit(url)
# param_2 = obj.back(steps)
# param_3 = obj.forward(steps)
```