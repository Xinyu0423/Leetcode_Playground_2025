# Solution 1
```Python
class Solution(object):
    def minimumDeletions(self, s):
        """
        :type s: str
        :rtype: int
        """
        stack = []
        res = 0
        for char in s:
            if char == 'b':
                stack.append(char)
            elif char == 'a' and len(stack) > 0 and stack[-1] =='b':
                res += 1
                stack.pop()
        return res
        
```