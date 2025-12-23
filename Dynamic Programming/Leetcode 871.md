# Solution 1
```Python
class Solution:
    def minRefuelStops(self, target: int, startFuel: int, stations: List[List[int]]) -> int:
        dp = [0 for _ in range(len(stations) + 1)]
        dp[0] = startFuel
        for i in range(len(stations)):
            for j in range(i, -1, -1):
                if dp[j] >= stations[i][0]:
                    dp[j + 1] = max(dp[j + 1], dp[j] + stations[i][1])
        for i in range(len(dp)):
            if dp[i] >= target:
                return i
        return -1      
```