# Solution 1
```Python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        n = len(nums)
        nums.sort()
        for i in range(n - 1):
            if nums[i + 1] == nums[i]:
                return True
        return False
```

# Solution 2
```Python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums_dict = {}
        for num in nums:
            if num not in nums_dict:
                nums_dict[num] = 1
            else:
                return True
        return False
```