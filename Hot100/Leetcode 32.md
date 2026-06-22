# Solution 1(暴力枚举，会超时)
```Python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        n = len(s)
        max_length = 0
        for i in range(n):
            count = 0
            for j in range(i, n):
                if s[j] == '(':
                    count += 1
                else:
                    count -= 1
                if count < 0:
                    break
                if count == 0:
                    max_length = max(max_length, j - i + 1)
        return max_length
```

# Solution 2(栈)
```Python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        stack = [-1]
        max_length = 0
        for i in range(len(s)):
            if s[i] == '(':
                stack.append(i)
            else:
                popped_element = stack.pop()
                if len(stack) == 0:
                    stack.append(i)
                else:
                    max_length = max(max_length, i - stack[-1])
        return max_length
```

# Solution 3(动态规划)
```Python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        if not s:
            return 0
        n = len(s)
        dp = [0 for _ in range(n)]
        for i in range(1, n):
            if s[i] == ')':
                if s[i - 1] == '(' and i - 2 >= 0:
                    dp[i] = dp[i - 2] + 2
                else:
                    pos = i - dp[i - 1] - 1
                    if pos < 0 or s[pos] != '(':
                        dp[i] = 0
                    else:
                        if pos - 1 >= 0:
                            dp[i] = dp[i - 1] + 2 + dp[pos - 1]
                        else:
                            dp[i] = dp[i - 1] + 2
        return max(dp)
```