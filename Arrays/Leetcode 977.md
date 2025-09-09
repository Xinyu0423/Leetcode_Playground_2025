# Solution 1:
```Python
class Solution(object):
    def sortedSquares(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        for i in range(len(nums)):
            nums[i] = nums[i] * nums[i]
        min_num = min(nums)
        min_index = nums.index(min_num)
        i = min_index - 1
        j = min_index + 1
        res = [min_num]
        while i >= 0 and j < len(nums):
            if nums[i] <= nums[j]:
                res.append(nums[i])
                i -= 1
            else:
                res.append(nums[j])
                j += 1
        while i >= 0:
            res.append(nums[i])
            i -= 1
        while j < len(nums):
            res.append(nums[j])
            j += 1
        return res
```