# Solution 1
```Python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        n = len(s)
        dp = [False for _ in range(n + 1)]
        dp[0] = True
        for i in range(1, n + 1):
            for j in range(i):
                if dp[j] and s[j:i] in wordDict:
                    dp[i] = True
                    break
        return dp[-1]
```

# Solution 2
```Python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        n = len(s)
        dp = [[False for _ in range(n + 1)] for _ in range(n + 1)]
        for i in range(n + 1):
            dp[i][i] = True
        for length in range(1, n + 1):
            for i in range(n - length + 1):
                j = i + length
                if s[i:j] in wordDict:
                    dp[i][j] = True
                for k in range(i + 1, j):
                    if dp[i][k] and dp[k][j]:
                        dp[i][j] = True
        return dp[0][-1]       
```