# Solution 1
```Python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        if len(nums) == 0:
            return [-1, -1]
        left_index = self.search_left(nums,target)
        if left_index == -1:
            return [-1, -1]
        right_index = self.search_right(nums, target)
        return [left_index, right_index]
       
    def search_left(self, nums, target):
        n = len(nums)
        left = 0
        right = n - 1
        while left < right:
            mid = (left + right) // 2
            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid
        if nums[left] == target:
            return left
        else:
            return -1

    def search_right(self, nums, target):
        n = len(nums)
        left = 0
        right = n - 1
        while left < right:
            mid = (left + right + 1) // 2
            if nums[mid] <= target:
                left = mid
            else:
                right = mid - 1
        if nums[right] == target:
            return right
        else:
            return -1
```