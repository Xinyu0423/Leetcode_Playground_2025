# Solution 1
```Python
class Solution:
    def maxProfit(self, prices: list[int]) -> int:
        # every day's max profit = today's stock price - the previous n days minium stock price 
        # all max profit = max(every day's max profit, all max profit)
        # we gonna do it backward
        maxProfit = float('-inf')
        every_day_max = prices[-1]
        for i in range(len(prices) - 2, -1, -1):
            every_day_max = max(every_day_max, prices[i])
            profit =  every_day_max - prices[i]

            maxProfit = max(maxProfit, profit)
           
        if maxProfit < 0:
            return 0
        return maxProfit
        
```
