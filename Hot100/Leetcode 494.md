# Solution 1
```Python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        nums_sum = sum(nums)
        if (nums_sum + target) % 2 == 1 or (nums_sum + target) / 2 < 0:
            return 0 
        n = len(nums)
        target = (nums_sum + target) // 2
        dp = [[0 for _ in range(target + 1)] for _ in range(n + 1)]
        dp[0][0] = 1
        for i in range(1, n + 1):
            for j in range(target + 1):
                if j >= nums[i - 1]:
                    dp[i][j] = dp[i-1][j] + dp[i-1][j - nums[i-1]]
                else:
                    dp[i][j] = dp[i - 1][j]
        return dp[-1][-1]       
```