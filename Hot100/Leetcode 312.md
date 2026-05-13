# Solution 1
```Python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        new_nums = [1] + nums + [1]
        n = len(new_nums)
        dp = [[0 for _  in range(n)] for _ in range(n)]
        for length in range(2, n):
            
            for left in range(n - length):
                right = left + length
                for k in range(left + 1, right):
                    dp[left][right] = max(dp[left][right], dp[left][k] + dp[k][right] + new_nums[left] * new_nums[right]* new_nums[k]) 
        return dp[0][-1]
```