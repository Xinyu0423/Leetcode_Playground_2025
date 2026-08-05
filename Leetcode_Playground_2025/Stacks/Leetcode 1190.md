# Solution 1
```Python
class Solution(object):
    def reverseParentheses(self, s):
        """
        :type s: str
        :rtype: str
        """
        stack = []
        res = ""
        for i in range(len(s)):
            if s[i] == '(':
                stack.append(res)
                res = ""
            elif s[i] == ')':
                res = res[::-1]
                res = stack[-1] +res
                stack.pop()
            else:
                res += s[i]
        return res

```