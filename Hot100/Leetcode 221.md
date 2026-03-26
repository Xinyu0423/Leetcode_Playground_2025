# Solution 1
```Python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        m = len(matrix)
        n = len(matrix[0])
        dp = [[0 for _ in range(n)] for _ in range(m)]
        res = 0 
        for i in range(m):
            if matrix[i][0] == '1':
                res = 1
                dp[i][0] = 1
        for j in range(n):
            if matrix[0][j] == '1':
                res = 1
                dp[0][j] = 1
                  
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == '1':
                    if i > 0 and j > 0:
                        dp[i][j] = min(dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1]) + 1
                        res = max(res, dp[i][j])
        return res * res        
```