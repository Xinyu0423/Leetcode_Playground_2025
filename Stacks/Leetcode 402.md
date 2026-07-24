# Solution 1
```Python
class Solution(object):
    def removeKdigits(self, num, k):
        """
        :type num: str
        :type k: int
        :rtype: str
        """
        stack = []
        for i in range(len(num)):
            while len(stack) > 0 and int(num[stack[-1]]) > int(num[i]) and k > 0:
                poped_element = stack.pop()
                k -= 1
            stack.append(i)
        while k > 0 and len(stack) > 0:
            stack.pop()
            k -= 1
        res = ''
        for index in stack:
            res += num[index]
        if len(res) == 0:
            return '0'
        return str(int(res))
```