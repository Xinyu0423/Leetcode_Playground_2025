# Solution 1
```Python
class Solution:
    def mergeStones(self, stones: List[int], k: int) -> int:
        if (len(stones) - 1) % (k - 1) != 0:
            return -1
        prefix_sum = [0 for _ in range(len(stones) + 1)]
        for i in range(len(stones)):
            prefix_sum[i + 1] = prefix_sum[i] + stones[i]
        dp = [[[float('inf') for _ in range(k + 1)] for _ in range(len(stones))] for _ in range(len(stones))]
        for i in range(len(stones)):
            dp[i][i][1] = 0
        for length in range(2, len(stones) + 1):
            for i in range(len(stones) - length + 1):
                j = i + length - 1
                temp_sum = prefix_sum[j + 1] - prefix_sum[i]
                for p in range(2, min(length, k) + 1):
                    if (length - p) % (k - 1) !=0:
                        continue
                    for m in range(i, j):
                        dp[i][j][p] = min(dp[i][j][p], dp[i][m][1] + dp[m + 1][j][p - 1])
                if (length - 1) % (k - 1) == 0:
                    if dp[i][j][k] != float('inf'):
                        dp[i][j][1] = dp[i][j][k] + temp_sum
        if dp[0][-1][1] == float('inf'):
            return -1
        else:
            return dp[0][-1][1]
```