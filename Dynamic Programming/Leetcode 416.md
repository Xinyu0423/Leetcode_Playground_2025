# Solution 1
```Python
class Solution(object):
    def canPartition(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        sum_nums = sum(nums)
        max_nums = max(nums)
        if sum_nums % 2 == 1:
            return False
        dp = [[0 for _ in range((sum_nums // 2) + 1)] for _ in range(len(nums) + 1)]
        for i in range(1, len(nums) + 1):
            for j in range((sum_nums//2) + 1):
                if j < nums[i - 1]:
                    dp[i][j] = dp[i -1][j]
                else:
                    dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - nums[i - 1]] + nums[i - 1])
        return dp[-1][(sum_nums//2)] == (sum_nums//2)
```

# Solution 2
```Python
class Solution(object):
    def canPartition(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        sum_nums = sum(nums)
        if sum_nums % 2 == 1:
            return False
        target = sum_nums / 2
        dp = [False for _ in range(target + 1)]
        dp[0] = True
        for i in range(1, len(nums) + 1):
            for j in range(target, -1, -1):
                if j >= nums[i - 1]:
                    dp[j] = dp[j] or dp[j - nums[i - 1]]
        return dp[-1]       
```