# Solution
```Python
class TextEditor(object):

    def __init__(self):
        self.left_stack = []
        self.right_stack = []
        

    def addText(self, text):
        """
        :type text: str
        :rtype: None
        """
        for char in text:
            self.left_stack.append(char)

        

    def deleteText(self, k):
        """
        :type k: int
        :rtype: int
        """
        count = 0
        for i in range(k):
            if len(self.left_stack) > 0:
                self.left_stack.pop()
                count += 1
            if count == k:
                break
        return count
        
        

    def cursorLeft(self, k):
        """
        :type k: int
        :rtype: str
        """
        min_k = min(k, len(self.left_stack))
        for _ in range(min_k):
            poped_element = self.left_stack.pop()
            self.right_stack.append(poped_element)
        if len(self.left_stack) >= 10:
            return ''.join(self.left_stack[len(self.left_stack) - 10:])
        else:
            return ''.join(self.left_stack)
        
        

    def cursorRight(self, k):
        """
        :type k: int
        :rtype: str
        """
        min_k = min(k, len(self.right_stack))
        for _ in range(min_k):
            poped_element = self.right_stack.pop()
            self.left_stack.append(poped_element)
        if len(self.left_stack) >= 10:
            return ''.join(self.left_stack[len(self.left_stack) - 10:])
        else:
            return ''.join(self.left_stack)


# Your TextEditor object will be instantiated and called as such:
# obj = TextEditor()
# obj.addText(text)
# param_2 = obj.deleteText(k)
# param_3 = obj.cursorLeft(k)
# param_4 = obj.cursorRight(k)
```