# Solution 1
```Python
class Solution:
    def numSquares(self, n: int) -> int:
        dp = [float('inf') for _ in range(n + 1)]
        dp[0] = 0
        for i in range(n + 1):
            for j in range(1, n + 1):
                if j * j <= i:
                    dp[i] = min(dp[i], dp[i - j * j ] + 1)
                else:
                    break
        return dp[-1]
```