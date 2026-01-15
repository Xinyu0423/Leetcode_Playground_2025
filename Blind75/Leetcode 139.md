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
        dp = [[False for _ in range(n)] for _ in range(n)]
        for length in range(1, n + 1):
            for i in range(n - length + 1):
                j = i + length - 1
                if s[i:j + 1] in wordDict:
                    dp[i][j] = True
                
                for k in range(i, j):
                    if dp[i][k]  and dp[k + 1][j]:
                        dp[i][j] = True 
        return dp[0][-1]            
```