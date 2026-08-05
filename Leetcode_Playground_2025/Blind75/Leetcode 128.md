# Solution 1
```Python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        nums_map = {}
        for num in nums:
            if num not in nums_map:
                nums_map[num] = 1
        res = 0
        for num in nums_map.keys():
            if num - 1 not in nums_map:
                temp_res = 1
                temp_num = num
                while temp_num + 1 in nums_map:
                    temp_num += 1
                    temp_res += 1
                res = max(temp_res, res)
        return res
```