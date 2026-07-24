# Solution 1
```Python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        n = len(nums)
        left = 1
        right = n
        while left < right:
            mid = (left + right) // 2
            count = self.count_smaller(nums, mid)
            if count > mid:
                right = mid
            else:
                left = mid +1
        return left
    
    def count_smaller(self, nums, mid):
        count = 0
        for num in nums:
            if num <= mid:
                count += 1
        return count
```