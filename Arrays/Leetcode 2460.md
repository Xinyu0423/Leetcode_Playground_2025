# Soultion 1:
```Python
class Solution(object):
    def applyOperations(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        k = 0 
        for i in range(len(nums)):
            if i + 1 < len(nums) and nums[i] == nums[i+1]:
                nums[i] = 2*nums[i]
                nums[i+1] =0

        for i in range(len(nums)):
            if nums[i] !=0:
                nums[k] = nums[i]
                k += 1

        for i in range(k, len(nums)):
            nums[i] = 0
        return nums
```

# Soultion 2:
```Python
class Solution(object):
    def applyOperations(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        k = 0
        for i in range(len(nums)):
            if i + 1 < len(nums) and nums[i] == nums[i+1]:
                nums[i] = 2 * nums[i]
                nums[i+1] = 0
        
        for i in range(len(nums)):
            if nums[i] == 0:
                k += 1
            else:
                nums[i - k] = nums[i]
        
        for i in range(len(nums) - k, len(nums)):
            nums[i] = 0
        return nums
```

# Soultion 3:
```Python
class Solution(object):
    def applyOperations(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        j = -1
        for i in range(len(nums)): 
            if i + 1 < len(nums) and nums[i] == nums[i+1]:
                nums[i] = 2 * nums[i]
                nums[i + 1] = 0

        for i in range(len(nums)):
            if nums[i] != 0:
                j += 1
                nums[i], nums[j] = nums[j], nums[i]
                
        for i in range(j + 1, len(nums)):
            nums[i] = 0
        return nums
```