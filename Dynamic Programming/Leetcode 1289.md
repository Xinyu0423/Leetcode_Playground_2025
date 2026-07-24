# Solution 1
```Python
class Solution(object):
    def minFallingPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        dp = [[0 for _ in range(len(grid[0]))] for _ in range(len(grid))]
        for j in range(len(grid[0])):
            dp[0][j] = grid[0][j]
        for i in range(1, len(grid)):
            for j in range(len(grid[0])):
                min_val = float("inf")
                for k in range(len(grid[0])):
                    if j == k:
                        continue
                    else:
                        min_val = min(dp[i - 1][k], min_val)
                dp[i][j] = min_val + grid[i][j]
        # print(dp)
        return min(dp[-1])
```