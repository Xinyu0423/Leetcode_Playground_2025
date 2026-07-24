# 解法1：
```Python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        k = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1
        return k
```

# 解法2：
```Python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        k = 0
        for i in range(len(nums)):
            if nums[i] == val:
                k += 1
            else:
                nums[i - k] = nums[i]
        return len(nums) -k
```

# 解法3：
```Python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        j = -1
        for i in range(len(nums)):
            if nums[i] != val:
                j += 1
                if j !=i:
                    nums[i], nums[j] = nums[j], nums[i]
        return j + 1
```