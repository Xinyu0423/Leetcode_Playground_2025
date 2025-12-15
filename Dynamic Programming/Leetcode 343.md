# Solution 1
```Python
class Solution(object):
    def integerBreak(self, n):
        """
        :type n: int
        :rtype: int
        """
        dp = [0 for _ in range(n + 1)]
        dp[2] = 1
        for i in range(2, n + 1):
            for j in range(i):
                dp[i] = max(dp[i],j * dp[i - j], j * (i - j))
        return dp[-1]

```