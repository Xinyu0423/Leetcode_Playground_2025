# Solution 1
```Python
class Solution(object):
    def makeGood(self, s):
        """
        :type s: str
        :rtype: str
        """
        stack = []
        for char in s:
            if len(stack) == 0:
                stack.append(char)
            elif char.islower() == True and stack[-1] == char.upper():
                stack.pop()
            elif char.isupper() == True and stack[-1] == char.lower():
                stack.pop()
            else:
                stack.append(char)
        return ''.join(stack)        
```