# Solution 1
```Python
class Solution(object):
    def findTargetSumWays(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        sum_nums = sum(nums)
        if sum_nums < abs(target) or (target + sum_nums) % 2 == 1:
            return 0
        sum_p = (target + sum_nums) / 2
        dp = [[0 for _ in range(sum_p + 1)] for _ in range(len(nums) + 1)]
        dp[0][0] = 1
        for i in range(1, len(nums) + 1):
            for j in range(sum_p + 1):
                dp[i][j] = dp[i - 1][j]
                if j >= nums[i - 1]:
                    dp[i][j] += dp[i -1][j - nums[i - 1]]
        return dp[-1][-1]
```