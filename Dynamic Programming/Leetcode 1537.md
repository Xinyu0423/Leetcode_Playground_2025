# Solution 1
```Python
class Solution(object):
    def maxSum(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: int
        """
        dp1 = [0 for _ in range(len(nums1) + 1)]
        dp2 = [0 for _ in range(len(nums2) + 1)]
        i = 1
        j = 1
        while i < len(nums1) + 1 or j < len(nums2) + 1:
            if i < len(nums1) + 1 and j < len(nums2) + 1:
                if nums1[i - 1] < nums2[j - 1]:
                    dp1[i] = dp1[i - 1] + nums1[i - 1]
                    i += 1
                elif nums1[i - 1] > nums2[j - 1]:
                    dp2[j] = dp2[j - 1] + nums2[j - 1]
                    j += 1
                else:
                    dp1[i] = max(dp1[i - 1] , dp2[j - 1]) + nums1[i - 1]
                    dp2[j] = max(dp1[i - 1] , dp2[j - 1]) + nums2[j - 1]
                    i += 1
                    j += 1
            elif i < len(nums1) + 1 and j >= len(nums2) + 1:
                dp1[i] = dp1[i - 1] + nums1[i - 1]
                i += 1
            elif i >= len(nums1) + 1 and j < len(nums2) + 1:
                dp2[j] = dp2[j - 1] + nums2[j - 1]
                j += 1
                

        return max(dp1[-1], dp2[-1]) % (10**9 + 7)
```