# Solution 1
```Python
class Solution:
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        reverse_point = -1
        n = len(nums)
        for i in range(n - 2, -1, -1):
            if nums[i] < nums[i + 1]:
                reverse_point = i
                break
        if reverse_point == -1:
            left = 0
            right = n -1
            while left < right:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
                right -= 1
        else:
            for i in range(n - 1, reverse_point, -1):
                if nums[i] > nums[reverse_point]:
                    nums[i], nums[reverse_point] = nums[reverse_point], nums[i]
                    break
            left = reverse_point + 1
            right = n - 1
            while left < right:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
                right -= 1
```