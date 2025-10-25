# Solution 1
```Python
class Solution(object):
    def evalRPN(self, tokens):
        """
        :type tokens: List[str]
        :rtype: int
        """
        if len(tokens) == 1:
            return int(tokens[0])
        stack = []
        res = 0
        for i in range(len(tokens)):
            if tokens[i] in ['+', '-', '*', '/']:
                num1 = stack.pop()
                num2 = stack.pop()
                if tokens[i] == '+':
                    res = num1 + num2
                    stack.append(res)
                elif tokens[i] == '-':
                    res = num2 - num1
                    stack.append(res)
                elif tokens[i] == '*':
                    res = num1 * num2
                    stack.append(res)
                elif tokens[i] == '/':
                    res = int(num2 / float(num1))
                    stack.append(res)
            else:
                stack.append(int(tokens[i]))
        return res
```