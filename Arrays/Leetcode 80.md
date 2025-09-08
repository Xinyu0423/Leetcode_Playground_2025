# Solution 1:
```Python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        k = 2
        for i in range(2, len(nums)):
            if not (nums[k - 2] == nums[k - 1] and nums[i] == nums[k - 1]):
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
        for i in range(2, len(nums)):
            if nums[i - k - 2] == nums[i - k - 1] and nums[i] == nums[i - k - 1]:
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
        j = 1
        for i in range(2, len(nums)):
            if not (nums[j - 1] == nums[j] and nums[i] == nums[j]):
                j += 1
                nums[j], nums[i] = nums[i], nums[j]
        return j + 1
```