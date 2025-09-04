# Solution 1:
```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        k=0
        for i in range(len(nums)):
            if nums[i] != 0:
                nums[k] = nums[i]
                k += 1
        for i in range(k, len(nums)):
            nums[i] = 0
        return nums
```

# Soultion 2:
```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        k = 0
        for i in range(len(nums)):
            if nums[i] == 0:
                k += 1
            else:
                nums[i - k] = nums[i]
        for i in range(len(nums) - k, len(nums)):
            nums[i] = 0
        return nums
```

# Solution 3:
```Python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        j = -1
        for i in range(len(nums)):
            if nums[i] != 0:
                j += 1
                if j !=i:
                    nums[i], nums[j] = nums[j], nums[i]
        return nums
```