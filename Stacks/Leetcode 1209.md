# Solution 1
```Python
class Solution(object):
    def removeDuplicates(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: str
        """
        stack = []
        res = ''
        for i in range(len(s)):
            if len(stack) > 0 and stack[-1][0] == s[i]:
                stack[-1][1] += 1
                if stack[-1][1] == k:
                    stack.pop()
            else:
                stack.append([s[i], 1])
        for i in range(len(stack)):
            for j in range(stack[i][1]):
                res += stack[i][0]
        return res
```