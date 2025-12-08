# Solution 1
```Python
class Solution(object):
    def findSubsequences(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        dp = [set() for _ in range(len(nums))]
        res = set()
        for i in range(len(nums)):
            dp[i].add((nums[i],))
            for j in range(i):
                if nums[i] >= nums[j]:
                    for seq in dp[j]:
                        dp[i].add(seq + (nums[i],))
            for seq in dp[i]:
                if len(seq) >= 2:
                    res.add(seq)
        return [list(seq) for seq in res]
```