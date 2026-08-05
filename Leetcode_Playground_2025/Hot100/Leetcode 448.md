# Solution 1
```Python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        n = len(nums)
        res = []
        for num in nums:
            x = (num - 1) % n
            nums[x] += n
        for i in range(n):
            if nums[i] <= n:
                res.append(i + 1)
        return res
```