# Solution 1
```Python
class Solution:
    def findUnsortedSubarray(self, nums: List[int]) -> int:
        sorted_nums = sorted(nums)
        n = len(nums)
        left_index = 0
        right_index = 0
        for i in range(n):
            if nums[i] != sorted_nums[i]:
                left_index = i
                break
        for i in range(n -1, -1, -1):
            if nums[i] != sorted_nums[i]:
                right_index = i
                break
        if right_index!= left_index:
            return right_index - left_index + 1
        return 0
```

# Solution 2
```Python
class Solution:
    def findUnsortedSubarray(self, nums: List[int]) -> int:
        left_index, right_index = 0, 0
        max_seen, min_seen =float('-inf'), float('inf')
        n = len(nums)
        for i in range(n):
            if nums[i] < max_seen:
                right_index = i
            max_seen = max(nums[i], max_seen)
        
        for i in range(n - 1, -1, -1):
            if nums[i] > min_seen:
                left_index = i
            min_seen = min(min_seen, nums[i])
        if right_index == 0:
            return 0
        return right_index - left_index + 1
```