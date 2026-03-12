# Solution 1
```Python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        max_profit = 0
        max_future = prices[-1]
        for i in range(n - 2, -1, -1):
            profit = max_future - prices[i]
            max_profit = max(max_profit, profit)
            max_future = max(max_future, prices[i])
        return max_profit
```