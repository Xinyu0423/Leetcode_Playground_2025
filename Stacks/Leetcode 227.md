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
        prev_op = '+'
        for i in range(len(s)):
            if s[i] in ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']:
                num = num * 10 + int(s[i])
            if s[i] in ['+', '-', '*', '/'] or i == len(s) -1:
                if prev_op == '+':
                    stack.append(num)
                elif prev_op == '-':
                    stack.append(-num)
                elif prev_op == '*':
                    poped_element = stack.pop()
                    stack.append(poped_element * num)
                elif prev_op == '/':
                    poped_element = stack.pop()
                    stack.append(int(poped_element / float(num)))
                
                if s[i] in  ['+', '-', '*', '/']:
                    prev_op = s[i]
                num = 0
        return sum(stack)
```