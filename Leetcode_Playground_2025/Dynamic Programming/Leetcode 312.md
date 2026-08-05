# Solution 1
```Python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        new_nums = [1] + nums + [1]
        dp = [[0 for _ in range(len(new_nums))] for _ in range(len(new_nums))]
        for length in range(2, len(new_nums)):
            for i in range(0, len(new_nums) - length):
                j = i + length
                for k in range(i + 1, j ):
                    dp[i][j] = max(dp[i][j], dp[i][k] + dp[k][j] + new_nums[i]* new_nums[j]*new_nums[k])
        # print(dp)
        return dp[0][-1]
```