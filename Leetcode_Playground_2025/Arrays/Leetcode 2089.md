# Solution 1
```Python
class Solution(object):
    def targetIndices(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        nums.sort()
        res = []
        for i in range(len(nums)):
            if nums[i] == target:
                res.append(i)
        return res
```

# Solution 2
```Python
class Solution(object):
    def targetIndices(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        count_smaller = 0
        count_equal = 0
        for i in range(len(nums)):
            if nums[i]  < target:
                count_smaller += 1
            elif nums[i] == target:
                count_equal += 1
        res = []
        for i in range(count_smaller, count_smaller + count_equal):
            res.append(i)
        return res
```