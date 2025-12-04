# Solution 1
```Python
class Solution(object):
    def maxTaxiEarnings(self, n, rides):
        """
        :type n: int
        :type rides: List[List[int]]
        :rtype: int
        """
        dp = [0 for _ in range(n + 1)]
        trip_map = {}
        for start, end, tip in rides:
            if start not in trip_map:
                trip_map[start] = [[end, tip]]
            else:
                trip_map[start].append([end, tip])
        for i in range(n):
            dp[i + 1] = max(dp[i + 1], dp[i])
            if i in trip_map:
                for end, tip in trip_map[i]:
                    dp[end] = max(dp[end], dp[i] + end - i + tip)
        return dp[-1]
```