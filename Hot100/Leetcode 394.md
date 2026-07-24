# Solution 1
```Python
class Solution:
    def decodeString(self, s: str) -> str:
        num_stack = []
        str_stack = []
        n = len(s)
        temp_num = 0
        res = ""
        for i in range(n):
            if s[i].isdigit():
                temp_num = temp_num * 10 +int(s[i])
            elif s[i] == '[':
                num_stack.append(temp_num)
                str_stack.append(res)
                temp_num = 0
                res = ""
            elif s[i] == ']':
                repeated_times = num_stack.pop()
                repeated_str = str_stack.pop()
                res = repeated_str + repeated_times * res
            else:
                res += s[i]
        return res
```