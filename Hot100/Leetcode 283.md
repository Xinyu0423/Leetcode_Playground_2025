# Solution 1
```Python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        # 遍历时记录0的个数，遇到不是0的就向前移，移动距离为当前0的个数
        # 遍历结束后，从 len(arr) - zeroCount 到末尾的所有位置都填上 0 即可。
        count_zero = 0
        n = len(nums)
        for i in range(n):
            if nums[i] == 0:
                count_zero += 1
            else:
                nums[i - count_zero] = nums[i]
        for i in range(1, count_zero + 1):
            nums[-i] = 0
```