# Solution 1
```Python
class Solution:
    def countSubstrings(self, s: str) -> int:
        n = len(s)
        dp = [[False for _ in range(n)] for _ in range(n)]
        res = 0
        for i in range(n - 1, -1, -1):
            for j in range(i, n):
                if s[i] != s[j]:
                    dp[i][j] = False
                    continue
                if s[i] == s[j]:
                    if i == j:
                        dp[i][j] = True
                        res += 1
                    elif j - i == 1:
                        dp[i][j] = True
                        res += 1
                    elif dp[i + 1][j - 1] == True:
                        dp[i][j] = True
                        res += 1
        return res
```