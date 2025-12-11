# Solution 1
```Python
class Solution(object):
    def tallestBillboard(self, rods):
        """
        :type rods: List[int]
        :rtype: int
        """
        sum_rods = sum(rods)
        dp = [[-1 for _ in range(sum_rods + 1)] for _ in range(len(rods) + 1)]
        dp[0][0] = 0
        for i in range(1, len(rods) + 1):
            rod = rods[i - 1]
            for j in range(sum_rods + 1):
                if dp[i-1][j] < 0:
                    continue
                # 不使用这根钢筋
                dp[i][j] = max(dp[i][j], dp[i - 1][j])
                # 把这根钢筋放在较高的柱子上
                if j + rod <= sum_rods:
                    dp[i][j + rod] = max(dp[i][j + rod], dp[i - 1][j])
                # 把这根钢筋放在较矮的柱子上
                # 即加上新的钢筋后，依然较低
                if rod <= j:
                    dp[i][j - rod] = max(dp[i - 1][j] + rod, dp[i][j - rod])
                # 即加上新的钢筋后，变成较高的了
                else:
                    dp[i][rod - j] = max(dp[i][rod - j], dp[i - 1][j] + j)
        return dp[-1][0]


```