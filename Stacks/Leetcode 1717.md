# Solution 1
```Python
class Solution(object):
    def maximumGain(self, s, x, y):
        """
        :type s: str
        :type x: int
        :type y: int
        :rtype: int
        """
        stack_1 = []
        res = 0
        if x <= y:
            for char in s:
                if len(stack_1) > 0 and stack_1[-1] == 'b' and char == 'a':
                    res += y
                    stack_1.pop()
                else:
                    stack_1.append(char)
        else:
            stack_1 = []
            for char in s:
                if len(stack_1) > 0 and stack_1[-1] == 'a' and char == 'b':
                    res += x
                    stack_1.pop()
                else:
                    stack_1.append(char)
        stack_2 = []
        if x <= y:
            for char in stack_1:
                if len(stack_2) > 0 and stack_2[-1] == 'a' and char == 'b':
                    res += x
                    stack_2.pop()
                else:
                    stack_2.append(char)
        else:
            for char in stack_1:
                if len(stack_2) > 0 and stack_2[-1] == 'b' and char == 'a':
                    res += y
                    stack_2.pop()
                else:
                    stack_2.append(char)
        return res
```