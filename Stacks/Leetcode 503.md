# Solution 1
```Python
class Solution(object):
    def nextGreaterElements(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        res = [-1 for _ in range(len(nums))]
        stack = []
        for i in range(len(nums)*2 - 1 ):
            while len(stack) > 0 and nums[stack[-1]] < nums[i % len(nums)]:
                res[stack[-1]] = nums[i % len(nums)]
                stack.pop()
            stack.append(i % len(nums))
        return res
```