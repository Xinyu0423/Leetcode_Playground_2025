# Solution 1
```Python
class Solution(object):
    def profitableSchemes(self, n, minProfit, group, profit):
        """
        :type n: int
        :type minProfit: int
        :type group: List[int]
        :type profit: List[int]
        :rtype: int
        """
        dp = [[0 for _ in range(minProfit + 1)] for _ in range(n + 1)]
        for i in range(n + 1):
            dp[i][0] = 1
        for index in range(len(group)):
            people = group[index]
            temp_profit = profit[index]
            for i in range(n, -1, -1):
                for j in range(minProfit, -1, -1):
                    if i - people >= 0:
                        dp[i][j] += dp[i - people][max(0, j - temp_profit)]
                        dp[i][j] %= (10**9) + 7
        return dp[-1][-1]
```