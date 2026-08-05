# Solution 1
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        n = len(nums)
        res = float('-inf')
        sums = 0
        l, r = 0, 0
        for r in range(n):
            sums += nums[r]
            while l < r and sums < nums[r]:
                sums -= nums[l]
                l += 1
            res = max(res, sums)
        return res
```

# Solution 2
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        n = len(nums)
        dp = [float('-inf')] * n 
        dp[0] = nums[0]
        for i in range(1, n):
            dp[i] = nums[i]
            dp[i] = max(dp[i], dp[i - 1] + nums[i])
        return max(dp)
```