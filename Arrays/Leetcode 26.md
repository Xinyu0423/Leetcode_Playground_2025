# Solution 1:
```Python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        k = 1
        for i in range(1, len(nums)):
            if nums[i] != nums[i -1]:
                nums[k] = nums[i]
                k += 1
        return k
```

# Solution 2:
```Python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        k = 0
        for i in range(1, len(nums)):
            if nums[i] == nums[i-1]:
                k += 1
            else:
                nums[i - k] = nums[i]
        return len(nums) - k
```

# Solution 3:
```Python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        j = 0
        for i in range(1, len(nums)):
            if nums[i] != nums[j]:
                j += 1
                nums[i], nums[j] = nums[j], nums[i]
        return j + 1
```