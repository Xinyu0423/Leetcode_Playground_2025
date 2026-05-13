# Solution 1
```Python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        # hold[i]：第 i 天结束后持有股票的最大利润。
        # sold[i]：第 i 天结束后不持有股票，且处于冷冻期（即当天刚卖出股票）的最大利润。
        # rest[i]：第 i 天结束后不持有股票，且不处于冷冻期（可以自由买入）的最大利润。
        hold = [0 for _ in range(n)]
        sold = [0 for _ in range(n)]
        rest = [0 for _ in range(n)]

        hold[0] = -prices[0]
        sold[0] = float('-inf')

        for i in range(1, n):
            # 保持前一天持有的股票，或者
            # 从非冷冻期的不持股状态买入（注意不能从冷冻期直接买入）。
            hold[i] = max(hold[i - 1], rest[i - 1] - prices[i])
            # 必须前一天持有股票，并在今天卖出（卖出后进入冷冻期）。
            sold[i] = hold[i - 1] + prices[i]
            # 保持前一天的非冷冻不持股状态，或者
            # 前一天是冷冻期（冷冻期结束后自然进入非冷冻不持股状态）。
            rest[i] = max(rest[i - 1], sold[i- 1])
        return max(sold[-1], rest[-1])
```