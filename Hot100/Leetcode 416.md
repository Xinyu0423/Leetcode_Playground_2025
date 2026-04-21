# Solution 1
```Python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        n = len(nums)
        nums_sum = sum(nums)
        if n < 2 or nums_sum % 2 == 1:
            return False
        target = int(nums_sum / 2)
        dp = [[False for _ in range(target + 1)] for _ in range(n)]
        for i in range(n):s
            dp[i][0] = True
        for i in range(n):
            for j in range(target + 1):
                if j >= nums[i]:
                    dp[i][j] = (dp[i - 1][j] or dp[i - 1][j - nums[i]])
                else:
                    dp[i][j] = dp[i - 1][j]
        return dp[n - 1][target]
```