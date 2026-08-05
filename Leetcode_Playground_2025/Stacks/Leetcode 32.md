# Solution 1
```Python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        max_count = 0
        stack = [-1]
        for i in range(len(s)):
            if s[i] == '(':
                stack.append(i)
            elif s[i] == ')':
                stack.pop()
                if len(stack) == 0:
                    stack.append(i)
                else:
                    max_count = max(max_count, i - stack[-1])
        return max_count
```