# Solution 1
```Python
class Solution:
    def strangePrinter(self, s: str) -> int:
        dp = [[0 for _ in range(len(s))] for _ in range(len(s))]
        for i in range(len(s)):
            dp[i][i] = 1
        for i in range(len(s) - 1, -1, -1):
            for j in range(i + 1, len(s)):
                dp[i][j] = dp[i + 1][j] + 1
                for k in range(i + 1, j + 1):
                    if s[i] == s[k]:
                        if k - 1 >= i + 1:
                            mid = dp[i + 1][k - 1]
                        else:
                            mid = 0
                        dp[i][j] = min(dp[i][j], mid + dp[k][j])
        return dp[0][-1]
        
```