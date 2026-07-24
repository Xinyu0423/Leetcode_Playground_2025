# Solution 1
```Python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        x = 0
        for i in range(len(nums)):
            if i <= x:
                x = max(x, i + nums[i])
                if x >= len(nums) - 1:
                    return True
        return False
```