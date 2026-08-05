# Solution 1
```Python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        next_greater_map = {}
        stack = []
        for i in range(len(nums2)):
            while len(stack) > 0 and stack[-1] < nums2[i]:
                next_greater_map[stack[-1]] = nums2[i]
                stack.pop()
            stack.append(nums2[i])
        res = [-1 for _ in range(len(nums1))]
        for i in range(len(nums1)):
            if nums1[i] not in next_greater_map:
                continue
            res[i] = next_greater_map[nums1[i]]
        return res
```