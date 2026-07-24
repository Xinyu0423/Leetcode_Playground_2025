# Solution 1
```Python
class Solution(object):
    def minRemoveToMakeValid(self, s):
        """
        :type s: str
        :rtype: str
        """
        stack = []
        for i in range(len(s)):
            if s[i] == '(' or s[i] == ')':
                stack.append(i)
            if len(stack) > 1 and s[stack[-1]] == ')' and s[stack [-2]] == '(':
                stack.pop()
                stack.pop()
        res = list(s)
        while len(stack) > 0:
            poped_element_index = stack.pop()
            res.pop(poped_element_index)
        return ''.join(res)
```