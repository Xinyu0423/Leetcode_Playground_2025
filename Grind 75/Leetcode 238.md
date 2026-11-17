# Solution 1
```Python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        prefix = [1 for _ in range(len(nums))]
        surfix = [1 for _ in range(len(nums))]
        for i in range(1, len(nums)):
            prefix[i] = prefix[i - 1] * nums[i - 1]
        for j in range(len(nums)- 2, -1, -1):
            surfix[j] = surfix[j + 1] * nums[j + 1]
        
        for i in range(len(nums)):
            nums[i] = prefix[i] * surfix[i]
        return nums
```
