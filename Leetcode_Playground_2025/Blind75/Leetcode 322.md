# Solution 1
```Python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        # dp[i][j] repsenting minimum coins using first i coins from coin list to reach the j amount
        # intialization
        # dp[0][0] we need to use 0 coin to reach 0 dollar
        # also for dp[1][0] to dp[i][0] all intialize to 0
        # also for dp[0][j] since we dont have any coins to use
        # it is impossible to have any coins to use, so we also set it to inifity
        # state transfer function
        # there r two case for each i(coin)
        # first one we not choose i coin dp[i][j] = dp[i - 1][j]
        # second one we choose use i coin
        # there r 2 subcases
        # if j < coins[i - 1] in that case we cannot use that coin, so dp[i][j] can only transfer from previous coin which is dp[i][j] = dp[i - 1][j]
        # else dp[i][j] = max(dp[i - 1][j], dp[i][j - coins[i - 1]] + 1)
        dp = [[0 for _ in range(amount + 1)] for _ in range(len(coins) + 1)]
        for j in range(amount + 1):
            dp[0][j] = float('inf')
        dp[0][0] = 0
        for i in range(1, len(coins) + 1):
            for j in range(1, amount + 1):
                dp[i][j] = dp[i - 1][j]
                if j - coins[i - 1] >= 0:
                    dp[i][j] = min(dp[i - 1][j], dp[i][j - coins[i - 1]] + 1)
        if dp[-1][-1] == float('inf'):
            return -1
        return dp[-1][-1]
```