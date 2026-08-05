# Solution 1
```Python
class Solution(object):
    def combinationSum4(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """

        dp = [0 for _ in range(target + 1)]
        dp[0] = 1
        for i in range(target + 1):
            for j in range(len(nums)):
                if i - nums[j] >= 0:
                    dp[i] += dp[i - nums[j]]
        return dp[-1]
```