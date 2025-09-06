# Solution 1:
```Python
class Solution(object):
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        # 遍历2次数组
        j = -1
        for i in range(len(nums)):
            if nums[i] == 0:
                j += 1
                nums[i], nums[j] = nums[j], nums[i]
        k = -1
        for i in range(j+1, len(nums)):
            if nums[i] == 1:
                k += 1
                nums[i], nums[k + j + 1] = nums[k + j + 1], nums[i]
```

# Solution 2:
```Python
class Solution(object):
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        i, j, k = 0, -1, len(nums)
        while i < k:
            if nums[i]  == 0:
                j += 1
                nums[i], nums[j] = nums[j], nums[i]
                i += 1
            elif nums[i] == 2:
                k -= 1
                nums[i], nums[k] = nums[k], nums[i]
            else:
                i += 1
```

# Solution 3:
```Python
class Solution(object):
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        x= [0, 0, 0]
        for i in nums:
            x[i] += 1
        k = 0
        for i in range(3):
            for j in range(x[i]):
                nums[k] = i
                k += 1
```