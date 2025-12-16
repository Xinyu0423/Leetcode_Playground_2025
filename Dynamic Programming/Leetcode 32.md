# Solution 1
```Python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        dp = [0 for _ in range(len(s))]
        if not s:
            return 0
        for i in range(1, len(s)):
            if s[i] == ')' and s[i - 1] == '(':
                if i < 2:
                    dp[i] = 2
                else:
                    dp[i] = dp[i - 2] + 2
            elif s[i] == ')' and i - dp[i -1] > 0 and s[i- dp[i - 1] - 1] == '(':
                dp[i] = 2 + dp[i -1] + dp[i - dp[i - 1] -2]
        return max(dp)
```