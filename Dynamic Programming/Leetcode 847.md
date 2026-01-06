# Solution 1
```Python
class Solution:
    def shortestPathLength(self, graph: List[List[int]]) -> int:
        n = len(graph)
        dist = [[float('inf') for _ in range(len(graph))] for _ in range(len(graph))]
        for i in range(len(graph)):
            dist[i][i] = 0
            for j in graph[i]:
                dist[i][j] = 1
        for k in range(n):
            for i in range(n):
                for j in range(n):
                    dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
        dp = [[float('inf') for _ in range(len(graph))] for _ in range(1<<n)]
        for i in range(n):
            dp[1<<i][i] = 0
        for mask in range(1 << n):
            for u in range(n):
                if dp[mask][u] == float('inf'):
                    continue
                for v in range(n):
                      if mask & (1 << v) == 0:
                        newMask = mask | (1 << v)
                        dp[newMask][v] = min(dp[newMask][v], dp[mask][u] + dist[u][v])
        fullMask = (1 << n) - 1
        res = float('inf')
        for i in range(n):
            res = min(res, dp[fullMask][i])
        return res
```