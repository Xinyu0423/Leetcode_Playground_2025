# Solution 1
```Python
class Solution(object):
    def findMaxForm(self, strs, m, n):
        """
        :type strs: List[str]
        :type m: int
        :type n: int
        :rtype: int
        """
        dp = [[0 for _ in range(n + 1)] for _ in range(m + 1)]
        for word in strs:
            zeros = word.count('0')
            ones = word.count('1')
            for i in range(m, -1, -1):
                for j in range(n, -1, -1):
                    if i - zeros >= 0 and j - ones >= 0:
                        dp[i][j] = max(dp[i][j], dp[i - zeros][j - ones] + 1)
        return dp[-1][-1]
```