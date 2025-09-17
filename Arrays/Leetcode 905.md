# Solution 1:
```Python
class Solution(object):
    def sortArrayByParity(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        j = -1
        for i in range(len(nums)):
            if nums[i] % 2 ==0:
                j += 1
                nums[i], nums[j] = nums[j], nums[i]
        return nums
```

# Solution 2:
```Python
class Solution(object):
    def sortArrayByParity(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        left = 0
        right = len(nums) - 1
        while left <= right:
            if nums[left] % 2 ==0:
                left += 1
            else:
                if nums[right] % 2 == 0:
                    nums[left], nums[right] = nums[right], nums[left]
                right -=1
        return nums
```