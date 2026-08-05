# Solution 1
```Python
class Solution:
    def checkIfPrerequisite(self, numCourses: int, prerequisites: List[List[int]], queries: List[List[int]]) -> List[bool]:
        dp = [[False for _ in range(numCourses)] for _ in range(numCourses)]
        for u, v in prerequisites:
            dp[u][v] = True
        print(dp)
        for k in range(numCourses):
            for i in range(numCourses):
                for j in range(numCourses):
                    dp[i][j] = dp[i][j] or (dp[i][k] and dp[k][j])
        res = []
        for u, v in queries:
            res.append(dp[u][v])
        return res
        
```