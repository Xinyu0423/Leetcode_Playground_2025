# Solution 1
```Python
class Solution(object):
    def checkValidString(self, s):
        """
        :type s: str
        :rtype: bool
        """
        parenthesis_stack = []
        star_stack = []
        for i in range(len(s)):
            if s[i] == '(':
                parenthesis_stack.append(i)
            elif s[i] == '*':
                star_stack.append(i)
            elif s[i] == ')':
                if len(parenthesis_stack) > 0:
                    parenthesis_stack.pop()
                elif len(star_stack) > 0:
                    star_stack.pop()
                else:
                    return False
        for i in range(len(parenthesis_stack)):
            if len(star_stack) > 0 and parenthesis_stack[-1] < star_stack[-1]:
                parenthesis_stack.pop()
                star_stack.pop()
        return len(parenthesis_stack) == 0
```