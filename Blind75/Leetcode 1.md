# Solution 1
```Python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_map = {}
        for i in range(len(nums)):
            nums_map[nums[i]] = i
        res = []
        for i in range(len(nums)):
            rest = target - nums[i]
            if rest in nums_map and nums_map[rest] != i:
                return [i, nums_map[rest]]
        return [-1, -1]
```