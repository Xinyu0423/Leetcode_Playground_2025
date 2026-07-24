# Solution 1
```Python
class Solution(object):
    def scoreOfParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        stack = [0]
        for i in range(len(s)):
            if s[i] == '(':
                stack.append(0)
            else:
                poped_element = stack.pop()
                if poped_element == 0:
                    stack[-1] += 1
                else:
                    stack[-1] += 2 * poped_element
        return stack[0]
```