# Solution 1
```Python
class Solution(object):
    def longestIncreasingPath(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: int
        """
        dp = [[1 for _ in range(len(matrix[0]))] for _ in range(len(matrix))]
        res = 0
        grid = []
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                grid.append([matrix[i][j], i, j])
        grid.sort(reverse = True)
        for val, i, j in grid:
            for dx, dy in [[1, 0], [-1, 0], [0, 1], [0, -1]]:
                x = i + dx
                y = j + dy
                if 0 <= x <len(matrix) and 0 <= y < len(matrix[0]) and matrix[x][y] > matrix[i][j]:
                    dp[i][j] = max(dp[i][j], dp[x][y] + 1)
            res = max(res, dp[i][j])
        return res
```