# Solution
```Python
class Solution(object):
    def robotWithString(self, s):
        """
        :type s: str
        :rtype: str
        """
        min_right = ['' for _ in range(len(s))]
        min_right[len(s) - 1] = s[-1]
        for i in range(len(s) - 2, -1, -1):
            min_right[i] = min(s[i], min_right[i + 1])
        # print(min_right)
        stack = []
        res = ''
        for i in range(len(s)):
            while len(stack) > 0 and s[stack[-1]] <= min_right[i]:
                poped_element = stack.pop()
                res += s[poped_element]
            stack.append(i)
        if len(stack)!= 0:
            for i in range(len(stack)):
                poped_element = stack.pop()
                res += s[poped_element]
        return res
```