# Solution 1
```Python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        n = len(nums)
        dp_min = [float('inf') for _ in range(n)]
        dp_max = [float('-inf') for _ in range(n)]
        dp_min[0] = dp_max[0] = nums[0]
        res = nums[0]
        for i in range(1, n):
            dp_max[i] = max(nums[i], dp_max[i - 1] * nums[i], dp_min[i - 1] * nums[i])
            dp_min[i] = min(nums[i], dp_max[i - 1] * nums[i], dp_min[i - 1] * nums[i])
            res = max(res, dp_max[i])
        return res
```