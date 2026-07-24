# Solution
```Python
class Solution:
    def numDecodings(self, s: str) -> int:
        if s[0] == '0':
            return 0
        res = 0
        n = len(s)
        if n == 1:
            return 1
        dp = [0 for _ in range(n)]
        dp[0] = 1
        if s[1] == '0' and (s[0] == '1' or s[0] == '2'):
            dp[1] = 1
        elif 10 <= int(s[:2]) <= 26:
            dp[1] = 2
        elif s[1] == '0' and int(s[:2]) > 26:
            return 0
        else:
            dp[1] = 1 
        for i in range(2, n):
            if s[i] != '0':
                dp[i] += dp[i - 1]
            if 10 <= int(s[i - 1 : i + 1]) <= 26:
                dp[i] += dp[i - 2]
        return dp[-1]
```