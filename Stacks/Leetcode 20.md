# Solution 1
```Python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = []
        for i in range(len(s)):
            stack.append(s[i])
            if len(stack) > 1:
                if stack[-2] == '(' and stack[-1] == ')':
                    stack.pop()
                    stack.pop()
                elif stack[-2] == '{' and stack[-1] == '}':
                    stack.pop()
                    stack.pop()
                elif stack[-2] == '[' and stack[-1] == ']':
                    stack.pop()
                    stack.pop()
            
        if len(stack) == 0:
            return True
        return False
```

# Solution 2
```Python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = []
        for i in range(len(s)):
            if s[i] == '(' or s[i] == '[' or s[i] == '{':
                stack.append(s[i])
            if s[i] == ')':
                if len(stack) == 0:
                    return False
                if stack[-1] != '(':
                    return False
                stack.pop()
            elif s[i] == ']':
                if len(stack) == 0:
                    return False
                if stack[-1] != '[':
                    return False
                stack.pop()
            elif s[i] == '}':
                if len(stack) == 0:
                    return False
                if stack[-1] != '{':
                    return False
                stack.pop() 
        if len(stack) == 0:
            return True
        else:
            return False
```

# Solution 3
```Python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        parentheses_map = {')' : '(', ']': '[', '}' : '{'}
        stack = []
        for i in range(len(s)):
            if len(stack) > 0 and s[i] in ([')', ']', '}'])and stack[-1] == parentheses_map[s[i]]:
                stack.pop()
            else:
                stack.append(s[i])
        return len(stack) == 0
```