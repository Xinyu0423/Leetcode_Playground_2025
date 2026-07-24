# Solution 1
```Python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s) < 2:
            return False
        if s[0] == ')' or s[0] == ']' or s[0] == '}':
            return False
        stack = []
        for char in s:
            if char == '(' or char == '[' or char == '{':
                stack.append(char)
            else:
                if char == ')' and (len(stack) == 0 or stack[-1] != '('):
                    return False
                elif char == ')' and stack[-1] == '(':
                    stack.pop()
                if char == ']' and (len(stack) == 0 or stack[-1] != '['):
                    return False
                elif char == ']' and stack[-1] == '[':
                    stack.pop()
                if char == '}' and (len(stack) == 0 or stack[-1] != '{' ):
                    return False
                elif char == '}' and stack[-1] == '{':
                    stack.pop()
                
        if not stack:
            return True
        else:
            return False
```