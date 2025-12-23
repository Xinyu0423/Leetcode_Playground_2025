# Solution 1
```Python
class Solution(object):
    def change(self, amount, coins):
        """
        :type amount: int
        :type coins: List[int]
        :rtype: int
        """
        dp = [0 for _ in range(amount + 1)]
        dp[0] = 1
        for i in range(len(coins)):
            for j in range(amount + 1):
                if j < coins[i]:
                    dp[j] = dp[j]
                else:
                    dp[j] = dp[j] + dp[j - coins[i]]
        return dp[-1]
```