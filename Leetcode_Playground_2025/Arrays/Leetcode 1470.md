# Solution 1
```Python
class Solution(object):
    def shuffle(self, nums, n):
        """
        :type nums: List[int]
        :type n: int
        :rtype: List[int]
        """
        res = []
        x_index = 0
        y_index = n
        while x_index < n:
            res.append(nums[x_index])
            res.append(nums[y_index])
            x_index += 1
            y_index += 1
        return res
        
```