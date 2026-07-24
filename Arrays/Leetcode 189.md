# Solution 1:
```Python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        if k > len(nums):
            k = k % len(nums)
        x = nums[0 : len(nums) - k]
        y = nums[len(nums) -k : ]
        x_prim = x[:: -1]
        y_prim = y[::-1]
        xy_prim = x_prim + y_prim
        nums[:] = xy_prim[::-1]
        return nums
```

