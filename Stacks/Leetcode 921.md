# Solution 1
```Python
class Solution(object):
    def minAddToMakeValid(self, s):
        """
        :type s: str
        :rtype: int
        """
        stack = []
        for i in range(len(s)):
            stack.append(s[i])
            if len(stack) > 1 and stack[-2] == '(' and stack[-1] == ')':
                stack.pop()
                stack.pop()
        return len(stack)
```