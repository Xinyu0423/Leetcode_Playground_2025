# Solution 1
```Python
class Solution(object):
    def findLength(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: int
        """
        dp = [[0 for _ in range(len(nums2))] for _ in range(len(nums1))]
        res = 0
        for i in range(len(nums1)):
            if nums1[i] == nums2[0]:
                dp[i][0] = 1
                res = 1
        for j in range(len(nums2)):
            if nums1[0] == nums2[j]:
                dp[0][j] = 1
                res = 1
        for i in range(1, len(nums1)):
            for j in range(1, len(nums2)):
                if nums1[i] != nums2[j]:
                    dp[i][j] = 0
                else:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                    res = max(res, dp[i][j])
        return res
```