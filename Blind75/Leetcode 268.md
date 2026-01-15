# Solution 1
```Python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        nums = set(nums)
        for i in range(n + 1):
            if i not in nums:
                return i
        return -1
```

# Solution 2
```Python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        total_sum = (n * (n+ 1)) // 2
        return total_sum - sum(nums)
```