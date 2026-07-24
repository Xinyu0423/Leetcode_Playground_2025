# Solution 1
```Python
class Solution(object):
    def buildArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        ans = []
        for i in range(len(nums)):
            ans.append(nums[nums[i]])
        return ans
```

# Solution 2
```Python
class Solution(object):
    def buildArray(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        for i in range(len(nums)):
            nums[i] += nums[nums[i]] % 1000 *1000
        for i in range(len(nums)):
            nums[i] = nums[i] // 1000
        return nums
        
```