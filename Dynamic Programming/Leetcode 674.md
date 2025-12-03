# Solution 1
```Python
class Solution(object):
    def findLengthOfLCIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        dp = [1 for _ in range(len(nums))]

        for i in range(1, len(nums)):
            if nums[i] > nums[i - 1]:
                dp[i] = max(dp[i], dp[i - 1] + 1)
        return max(dp)
```