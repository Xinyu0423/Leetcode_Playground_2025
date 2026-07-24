# Solution 1
```Python
class Solution(object):
    def coinChange(self, coins, amount):
        """
        :type coins: List[int]
        :type amount: int
        :rtype: int
        """
        dp = [[0 for _ in range(amount + 1)] for _ in range(len(coins) + 1)]

        # dp[0][0] = 1
        for i in range(len(coins) + 1):
            dp[i][0] = 0
        for j in range(1, amount + 1):
            dp[0][j] = float('inf')
        # print(dp)
        for i in range(1, len(coins) + 1):
            for j in range(amount + 1):
                # dp[i][j] = dp[i - 1][j]
                if j - coins[i - 1] >=0:
                    dp[i][j] = min(dp[i - 1][j], dp[i][j - coins[i - 1]] + 1)
                else:
                    dp[i][j] = dp[i - 1][j]
        if dp[-1][-1] == float('inf'):
            return -1
        else:
            return dp[-1][-1]
```

# Solution 2
```Python
class Solution(object):
    def coinChange(self, coins, amount):
        """
        :type coins: List[int]
        :type amount: int
        :rtype: int
        """
        dp = [float('inf') for _ in range(amount + 1)]
        dp[0] = 0
        for i in range(1, len(coins) + 1):
            for j in range(amount + 1):
                if j - coins[i - 1] >= 0:
                    dp[j] = min(dp[j], dp[j - coins[i - 1]] + 1)
        if dp[-1] == float('inf'):
            return -1
        else:
            return dp[-1]
```