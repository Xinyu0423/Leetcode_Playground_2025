# Solution 1
```Python
class Solution(object):
    def calculate(self, s):
        """
        :type s: str
        :rtype: int
        """
        stack = []
        num = 0
        sign = 1
        res = 0
        for i in range(len(s)):
            if s[i] in ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']:
                num = num *10 + int(s[i])
            elif s[i] == '+' or s[i] =='-':
                res += sign * num
                num = 0
                if s[i] == '+':
                    sign = 1
                else:
                    sign = -1
            elif s[i] == '(':
                stack.append(res)
                stack.append(sign)
                res = 0
                num = 0
                sign = 1
            elif s[i] == ')':
                res += sign * num
                num = 0
                prev_sign = stack.pop()
                prev_res = stack.pop()
                res = prev_res + prev_sign * res
            elif s[i] == ' ':
                continue
        res += num * sign
        return res
```